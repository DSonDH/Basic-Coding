# Basic-Coding-Concepts
Summary of Basic Coding Concepts

Mainly refered to Pope Kim's POCU Academy curriculum.

## 1. Overall programming concepts

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

* 제곱 관련 loop돌면서 판별할 때 역으로 sqrt로 판별해버리면 loop 안돌아도 되는 경우가 있음  
  
* int(str, base) : str을 base 진법 수로 바꿔줌. base 기본값 10.
  
* map, lambda
```list(map(lambda x:x*x, range(1,6)))```  

