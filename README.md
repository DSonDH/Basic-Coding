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
포팅 문제 없는 값의 범위.  
unsigned short : 0~65535  
signed short : -32767 ~ 32767   

int : (C89표준) 최소 16비트이고 short 크기 이상인 정수형
int : 그냥 정수라는 의미. CPU에게 앞뒤 생략하고 정수처리하라고 하면 CPU가 아는 크기여야 함.  그 크기는?  
CPU의 ALU (Arithmetic Logic Unit)이 사용하는 기본 데이터 이 데이터를 word(워드)라 하고, 그 크기를 워드 크기라고 함  
워드 크기는 register크기랑 일치함. 즉 CPU따라 다르고, 옛날 당시엔 16bit CPU가 흔했음! 그뒤에 32bit컴퓨터가 나오면서 int 크기는 32비트가 됨 ! 지금 64bit이지만 32비트로 머묾. 64비트로 바군다고 성능이 무조건 빨라지지도 않음 (cache memory 때문)  

int의 리터럴(literal)  
'u' 혹은 'U': 부호없는(unsigned)수를 표현하는 접미사.
부호있는 수의 최댓값 보다 큰 값을 unsigned int에 대입할 경우 'u'혹은 'U'를 붙여야 함. 안붙이면 warning 발생  


long : 최소 32비트이고 int 이상의 크기. 다른 언어에서는 보통 64bit  
최소 64bit인 정수형은 C89에는 없다.  C89에서 int와 같음.
literal : 'l' 혹은 'L', 'ul' 혹은 'UL' (unsigned 표시)


<br>

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
