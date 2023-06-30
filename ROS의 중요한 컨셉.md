## Chapter 4. ROS의 중요 컨셉
2023 / 06 / 28  작성자 김소희


---
### 목차
1. ROS 용어 정리
2. 메시지 통신 (주요)
3. 메시지
4. 네임
5. 좌표 변환(TF)

---
### 1. ROS 용어 정리
1) Node : 최소 단위의 실행 가능한 프로세서로 하나의 실행 가능한 프로그램으로 생각하기.
각 노드는 메시지 통신으로 데이터를 주고 받는다.
2) Package : 하나 이상의 노드, 노드 실행을 위한 정보 등을 묶어 놓은 것 ex) 얼굴인식 프로그램
3) Message : 메시지를 통해 노드간의 데이터를 주고받게 된다.
메시지는 변수 형태(integer, floating point, boolean 등)

4) Topic, Publisher, Subscriber
   ![image](https://github.com/riseacademy/ROS-Study/assets/91440336/283771e7-17f6-48d6-adf5-c75229431876) topic은 단방향, 연속성 특징을 가짐. 따라서 일방적으로 데이터를 자꾸 보내야 하는 상황에 많이 사용됨.  publisher은 메시지를 보내는 역할. subscriber은 메시지를 받는 역할.
   
   
   
5) Service, Service server, Service client
   ![image](https://github.com/riseacademy/ROS-Study/assets/91440336/328f9605-c6ea-47d3-968c-cf27f1587580) service는 topic과 달리 양방향, 일회성 특징을 가짐. 로봇에 특정 동작 수행 명령할 때 사용됨. 

6) Action, Action server, Action client
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/df0a00d3-990e-4033-9148-b9f58e7acf35) action은 feedback 전송 후 최종 결과를 전달하는 역할. 복잡하고 장시간 걸리는 task에서 주로 사용됨. 

---

### 2. 메시지 통신 : ROS에서 가장 기본이 되는 기술
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/e69c559e-33b2-4186-aa7d-140113e9a46d)

1) 마스터 구동 :XMLRPC(XML-Remote Procedure Call)
```
$roscore
```
roscore는 기본 실행 명령어로써 package에서 하나의 노드를 실행하는데 사용된다. 노드의 개수에 상관없이 실행되는 각 노드들의 정보들을 관리하여 노드간의 통신을 연결시키는 역할을 한다. 

2) 서브스크라이버 노드 구동
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/8f1ccbc8-b375-4403-9fbb-130e7117735a)

```
$roscore 패키지이름 노드이름
```
노드의 이름, 전송할 topic의 이름, 전송할 message의 형태, 노드의 IP, port의 번호 등을 master에게 전달한다. 

3) 퍼블리셔 노드 구동
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/43f2c8dc-292d-406d-93e8-36c3d1e08ca9)

```
$rosrun 패키지이름 노드이름
```

4) 퍼블리셔 정보 알림
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/4c9d1e68-9bae-4a09-b348-9b095cf41e89)

마스터는 서브스크라이버 노드에게 새로운 퍼블리셔 정보를 전달한다.

5) 퍼블리셔 노드에 접속 요청
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/2e6018ca-a3d7-4e66-917d-f24fcd85c362)

마스터로부터 받은 퍼블리셔 정보를 이용하여 TCPROS 접속을 요청
6) 서브스크라이버 노드에 접속 응답
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/d32907ec-778d-4f6f-9d3b-4cb6e8a70366)

접속 응답에 해당되는 자신의 TCP URI 주소와 Port 번호 전송
7) TCP 접속
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/1a8ab236-d9d4-419a-ab40-0d65d213621d)

TCPROS를 이용하여 Subscriber node가 Publisher node와 직접 연결
8) 메시지 전송
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/c55c215f-7fdc-4b39-be28-981902e91060)

발행자 노드는 서브스크라이버 노드에게 메시지를 전송(토픽)
9) 서비스 요청 및 응답
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/4b4b64cc-8fa7-4b24-9f3e-a4dcfd97e031)

1회에 한해 접속, 서비스 요청 및 서비스 응답이 수행된 후 서로간의 접속을 끊는다.

---

### 3. 메시지

```
$rosrun turtlesim turtlesim_node
```
rosrun은 노드 하나를 실행시킬 때 사용된다.
<br/>
위의 코드는 turtlesim이라는 package 안에 있는 turtlesim node를 실행시키라는 코드이다. 
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/d66cb599-e6ed-46b1-806a-704539ef1b85)
<br/>
Parameter은 그로벌 변수를 네트워크에 지정한 후에 외부에서 변경시키고 다른 노드에서 받아서 process를 바꿀 수 있다.



---

### 4. 네임
노드와 메시지(토픽, 서비스, 액션, 파라미터)가 가지는 고유의 식별자

---

### 5. 좌표 변환(TF)
각 joint들의 상대 좌표 변환
상대 좌표로 서로 연결되어 있는 각 로봇 관절의 움직임을 어떻게 모델링할 것인가?

