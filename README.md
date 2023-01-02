# Basic-Coding-Concepts
Summary of Basic Coding Concepts

## 1. Overall programming concepts

### C  
```#include```는 전처리기 지시문 중 하나.  
전처리기(preprocessor) : 컴파일 하기 전 테스트를 복붙해주는 역할을 함.  
```#include <stdio.h>```가 정확한 문법. "stdio.h"도 되나, 지양함.  
C 표준 라이브러리란 ? 문자열 처리, 수학 계산, 입출력 처리, 메모리 관리에 필요한 매크로, data type, 함수 등을 모아 놓은 것.  

```
int main(void)
{
    return 0;  /* 프로그램에 아무 문제가 없음을  알려주는 관례. 규약.*/
}
```  
함수 선언 : 
함수 선언에서 void 생략 : 매개변수 받는데, 매개변수 갯수와 자료형을 모르는 상태  
함수 정의에서 void 생략 : 매개변수가 없다는 뜻  
함수 정의, 선언에서 void : 매개변수가 없다는 뜻을 명시하는 것.  

<br>
## 2. Python notes

sort(item, key = lambda x: f(x))

### 타입별 내장함수
* string type
``` s.lower().count('p') ```  
!! string은 immutable 이므로 index별 재 allocation 불가능. 리스트로 바꾸면 가능.

* list  
pop : 해당 index 자리 제거  
remove : 해당 값 제일 왼쪽값 제거  

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
```list(map(lambda x:x*x, range(1,6)))```  

* collection module  
```
from collections import Counter
>>> Counter(["hi", "hey", "hi", "hi", "hello", "hey"])
Counter({'hi': 3, 'hey': 2, 'hello': 1})
```
