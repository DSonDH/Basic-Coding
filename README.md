# Basic-Coding-Concepts
Summary of Basic Coding Concepts

Mainly refered to Pope Kim's POCU Academy curriculum.

## 1. Overall programming concepts

## 2. Python notes

sort(item, key = lambda x: f(x))

### 타입별 내장함수
* string type
``` s.lower().count('p') ```
* list
* set
* dictionary

### 주의사항
* python for loop iterable data type change cause unexpected behavior  
for loop 돌도록 하는 변수를 loop 내에서 바꾸면 다음 루프에서 바뀐 아이로 실행되서 코딩이 어려워질 수 있음
![image](https://user-images.githubusercontent.com/15919242/206884883-dd7947f0-8383-40b5-81a9-4b594d46533b.png)

### 기타 팁 (?)
* python combination module  
![image](https://user-images.githubusercontent.com/15919242/206885055-05410248-b6ee-4fa2-813f-c244a668a120.png)

* 제곱 관련 loop돌면서 판별할 때 역으로 sqrt로 판별해버리면 loop 안돌아도 되는 경우가 있음  
