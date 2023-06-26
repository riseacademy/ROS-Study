# Chapter 7. ROS 기본 프로그래밍

## ROS 강의 Chapter 7 목차
1. ROS 프로그래밍 전에 알아둬야 할 사항
2. 퍼블리셔와 서브스크라이버 노드 작성 및 실행
3. 서비스 서버와 클라이언트 노드 작성 및 실행
4. 액션 서버와 클라이언트 노드 작성 및 실행
5. 파라미터 사용법
6. Roslaunch 사용법   

위의 목록 중 퍼블리셔와 서브스크라이버 노드 작성, 서비스 서버와 클라이언트 노드 작성에 대해 집중적으로 다룰 것이다.

### ROS 프로그래밍 전에 알아둬야 할 사항

#### ROS의 표준단위
ROS는 SI 단위를 사용해야한다.
|Quantity|Unit|
|--------|--------|
|angle|radian|
|frequency|hertz|
|force|newton|
|power|watt|
|voltage|volt|
|length|meter|
|mass|kilogram|
|time|second|
|current|ampere|
|temperature|celsius|    
#### ROS의 좌표 표현 방식
x:forward   
y:left   
z:up  
#### ROS의 프로그래밍 규칙
