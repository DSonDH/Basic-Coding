# Basic-Coding-Concepts
Summary of Basic Coding Concepts

## 1. Overall programming concepts

### C  
```#include```는 전처리기 지시문 중 하나.  
전처리기(preprocessor) : 컴파일 하기 전 테스트를 복붙해주는 역할을 함.  
```#include <stdio.h>```가 정확한 문법. "stdio.h"도 되나, 지양함.  
C 표준 라이브러리란 ? 문자열 처리, 수학 계산, 입출력 처리, 메모리 관리에 필요한 매크로, data type, 함수 등을 모아 놓은 것.  

```C
int main(void)
{
    return 0;  /* 프로그램에 아무 문제가 없음을  알려주는 관례. 규약.*/
}
```  
함수 선언 : 
함수 선언에서 void 생략 : 매개변수 받는데, 매개변수 갯수와 자료형을 모르는 상태  
함수 정의에서 void 생략 : 매개변수가 없다는 뜻  
함수 정의, 선언에서 void : 매개변수가 없다는 뜻을 명시하는 것.  

printf("%d + %d\n", num1, num2)  /* format 맞추기만 됨*/  

기본 자료형(primitive types)  
1byte = 8bit
char :
short
int
long
float
double
long double

```C
char default_char = 100;
signed char signed_char = -100;
unsigned char unsigned_char = 255;
int default_int = -10000;
signed int signed_int = -10000;
unsigned int unsigned_int = 234;

char ch_a = 'a';
char ch_b = ch_a + 1;
char ch_c = 99;
```
C에서 char 는 최소 8bit인 정수형이 표준임. 
signed/unsigned 생략시, C자체에서 정의는 하지 않는데 컴파일러에 따라 달라짐.  
char가 몇비트인지 찾는 방법  
<limits.h>헤더를 include한 뒤 CHAR_BIT보면 웬만하면 8비트인걸 확인할 수 있음  
소형기기에 따라 특정 크기를 사용하는게 어려울 수도 있으므로 CHAR_BIT에 정의된거에 의존함.  

ASCII는 0~127인 숫자  
컴파일러 따라 signed나 unsigned 생략했을 때 어떤건지 다름.  
Clang Windows에서는 생략 시 signed임.

char의 부호 여부 판단 방법  
<limit.h> 파일에서 CHAR_MIN을 보면 부호식변자가 없는 char가 signed인지 unsigned인지 알 수 있음  
범위 : 부호 없는 경우 0~255 (표준), 부호 있는 경우 : -128~127 (표준이면서 매우 올드한 기계에서는 -127~127)  

short : 최소 16비트이고 char의 크기 이상인 정수형, int의 반절.
(unsigned 명시 안하면 signed)  
포팅 문제 없는 값의 범위.  
unsigned short : 0~65535  
signed short : -32767 ~ 32767  

int : (C89표준) 최소 16비트이고 short 크기 이상인 정수형
(unsigned 명시 안하면 signed)  
int : 그냥 정수라는 의미. CPU에게 앞뒤 생략하고 정수처리하라고 하면 CPU가 아는 크기여야 함.  그 크기는?  
CPU의 ALU (Arithmetic Logic Unit)이 사용하는 기본 데이터 이 데이터를 word(워드)라 하고, 그 크기를 워드 크기라고 함  
워드 크기는 register크기랑 일치함. 즉 CPU따라 다르고, 옛날 당시엔 16bit CPU가 흔했음! 그뒤에 32bit컴퓨터가 나오면서 int 크기는 32비트가 됨 ! 지금 64bit이지만 32비트로 머묾. 64비트로 바군다고 성능이 무조건 빨라지지도 않음 (cache memory 때문)  

int의 리터럴(literal)  
'u' 혹은 'U': 부호없는(unsigned)수를 표현하는 접미사.
부호있는 수의 최댓값 보다 큰 값을 unsigned int에 대입할 경우 'u'혹은 'U'를 붙여야 함. 안붙이면 warning 발생  

long : 최소 32비트이고 int 이상의 크기. 다른 언어에서는 보통 64bit  
최소 64bit인 정수형은 C89에는 없다.  C89에서 int와 같음.
literal : 'l' 혹은 'L', 'ul' 혹은 'UL' (unsigned 표시)  

float : 보통 32bit인데 컴파일러 구현따라 다름, char 이상이면 됨  
``` C
float  num = 3.14f;
unsigned float unsigned_float = 3.14f; /* 컴파일오류 */
signed float signed_float = -3.14f;    /* 컴파일오류 */
float signed_float = -3.14uf;          /* 컴파일오류 */
```

double : 표준에 따르면 cpu가 계산에 사용하는 기본데이터 크기.  
크기는 float 이상이면 됨. 컴파일러 구현따라 다름, float처럼 unsigned형 없음.  

long double : double보다 정밀도가 높음. double이상 크기면 됨. unsigned형 없음.  

CF)  
porting : 다른 플랫폼으로 맞게 만드는 과정  
converting : 같은 플랫폼 상에서 개발 언어가 다른 경우  

C에서 boolean형은 없다. 0은 false, 0아닌 값은 true.  
관례상 return true 역할로 return 1을 많이 한다고 함.  

``` C
enum champ {
    CHAMP_ZED,  /* 관례 : enum 이름인 champ를 enum으로 만들 값 prefix로 박아줌*/
    CHAMP_JAX
};  /* CHAMP_ZED는 0, CHAMP_JAX는 1 정수형을 가지게 됨.*/
```

변수 선언은 블럭의 시작에서만 해야함. 코드 중간에서 int var_name = ~~~ 하면 컴파일 오류뜸.  
대신 블록 시작에서 선언만 int result;로 하고 코드 중간에서 result = add(n1, n2)하면 컴파일 됨.  

sizeof() 는 함수가 아니고 연산자다.  
피연산자의 크기를 바이트로 반환해주는 연산자!  
컴파일 중에 평가된다. 호출되는 함수가 아님.  
연산자가 반환하는 값은 부호없는 정수형 상수로 size_t형이다. (새로운 dtype 비슷함)  
음수 필요없는 index로 자주 쓰는 타입이라고 함.  
"_t" 는 typedef를 했다는 힌트. C89표준은 size_t 크기를 명시하지 않음. C99 표준에서 최소 16비트 요구함.  
```C
char ch = 'a';
size_t size_char = sizeof(ch);
```

* 배열의 경우, 함수 인자로 받을 경우 sizeof()결과는 4바이트임. 
```C
int num = 10;            
int* p = &num;            /* 역참조 연산자(X) 포인터 변수 선언 */
int num1 = *p;            /* 역참조 연산자(O) */
int result = num1 * num2; /* 역참조 연산자(X) 곱셈 연산자(O) */

주소연산자 &
int num = 10;
int* p = &num;
int still_num = num & num;  /* 주소 연산자(X) 비트 연산자(O) */
/* 피연산자가 하나일 때는 주소연산자. 피연산자가 2개일때 사용하는 비트 연산자가 아님
어떤 변수의 메모리 주소를 반환. */
```

* 조건문 은 if문 혹은 switch문을 말함. for문한에 있는 것은 조건식임 !!  
```C
float num = 3.14f;

if (num) {
    printf("%f\n", num);
}

/* case에 사용가능한 데이터형 : int, char, enum만 가능
break 안넣으면 그 아래코드 계속 실행함. 조건 확인도 안하고! 이를 fallthrough라 함 
근데 이를 일부러 유도한 걸수도 있으니까 주석으로 intentioanl fallthrough를 명시해야함 
case lable은 반드시 상수만 넣도록, 이 상수는 컴파일 시 결정되야하도록 언어 스펙이 정해짐 
즉 변수라서 계속 바뀔 가능성 있으면 안되는 것임.. */
switch (num) {
case 0:
    printf("Hello POCU!\n");
    break;
case 1:
    printf("Hello World!\n");
    break;
default:
    printf("The Others!\n");
    break;
}
```

C for loop, while, do while
```
int sum = 0;
size_t i;
for (i=0; i < 10; ++i) {
    sum += i;
}

int day = 5;
while (day-- > 0) {
    printf("%d\n", day);
    
    if (num < 1) {
        break;  /* continue; 도 사용가능 python과 동일 기능 */
    }
}

int day = 5;
do {
    printf("%d\n", day);
} while (day -- != 0);

코딩표준 : boolean 0이면 조건식 자동 판별이 되지만, == 0 !=0 을 명시해주자.
```

<br>
<br>
<br>
<br>
--------

## 2. Python notes

sort(item, key = lambda x: f(x))

### 타입별 내장함수
* string type
``` s.lower().count('p') ```  
!! string은 immutable 이므로 index별 재 allocation 불가능. 리스트로 바꾸면 가능.

```python3
'ooyyy'.count('y')
>>> 3
```  


* list  
pop : 해당 index 자리 제거  
remove : 해당 값 제일 왼쪽값 제거  
```python3
>>> a = [1, 1, 1, 2, 3]
>>> a.count(1)
3

>>> ['ox', 'o', 'x', 'oxoxox'].count('ox')
1
```


* set
* dictionary

### 주의사항
* python for loop iterable data type change cause unexpected behavior  
for loop 돌도록 하는 변수를 loop 내에서 바꾸면 다음 루프에서 바뀐 아이로 실행되서 코딩이 어려워질 수 있음
![image](https://user-images.githubusercontent.com/15919242/206884883-dd7947f0-8383-40b5-81a9-4b594d46533b.png)  
for loop 변수값을 바꾸던지/pop 등으로 길이 변경되게 하던지, 

### 기타 팁 (?)
* python combination module  
![image](https://user-images.githubusercontent.com/15919242/206885055-05410248-b6ee-4fa2-813f-c244a668a120.png)

* for -else 문은, for loop를 break하지 않으면 else가 실행되는 것임. for iterable data가 없을때 else가 실행되는게 아님.

* 제곱 관련 loop돌면서 판별할 때 역으로 sqrt로 판별해버리면 loop 안돌아도 되는 경우가 있음  
  
* int(str, base) : str을 base 진법 수로 바꿔줌. base 기본값 10.
  
* map, lambda
```python3
list(map(lambda x:x*x, range(1,6)))
```  

* collection module  
```python3
from collections import Counter
>>> Counter(["hi", "hey", "hi", "hi", "hello", "hey"])
Counter({'hi': 3, 'hey': 2, 'hello': 1})
```
