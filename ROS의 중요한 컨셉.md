## Chapter 4. ROS의 중요 컨셉
2023 / 06 / 28  작성자 김소희


---
### 목차
1. ROS 용어 정리
2. 메시지 통신
3. 메시지
4. 네임
5. 좌표 변환(TF)

---
### 1. ROS 용어 정리
1) Node : 최소 단위의 실행 가능한 프로세서로 하나의 실행 가능한 프로그램으로 생각하기.
각 노드는 메시지 통신으로 데이터를 주고 받는다.
2) Package : 하나 이상의 노드, 노드 실행을 위한 정보 등을 묶어 놓은 것
3) Message : 메시지를 통해 노드간의 데이터를 주고받게 된다.
메시지는 변수 형태(integer, floating point, boolean 등)

4) Topic, Publisher, Subscriber
   ![image](https://github.com/riseacademy/ROS-Study/assets/91440336/283771e7-17f6-48d6-adf5-c75229431876)
   
5) Service, Service server, Service client
   ![image](https://github.com/riseacademy/ROS-Study/assets/91440336/328f9605-c6ea-47d3-968c-cf27f1587580)

6) Action, Action server, Action client
![image](https://github.com/riseacademy/ROS-Study/assets/91440336/df0a00d3-990e-4033-9148-b9f58e7acf35)

### 2. 메시지 통신
1) 마스터 구동 :XMLRPC(XML-Remote Procedure Call)
# $roscore
2) 서브스크라이버 노드 구동
# $roscore 패키지이름 노드이름
3) 퍼블리셔 노드 구동
# $rosrun 패키지이름 노드이름
4) 퍼블리셔 정보 알림
마스터는 서브스크라이버 노드에게 새로운 퍼블리셔 정보를 알린다.
5) 퍼블리셔 노드에 접속 요청
마스터로부터 받은 퍼블리셔 정보를 이용하여 TCPROS 접속을 요청
6) 서브스크라이버 노드에 접속 응답
접속 응답에 해당되는 자신의 TCP URI 주소와 Port 번호 전송
7) TCP 접속
TCPROS를 이용하여 Subscriber node가 Publisher node와 직접 연결
8) 메시지 전송
발행자 노드는 서브스크라이버 노드에게 메시지를 전송(토픽)
9) 서비스 요청 및 응답
1회에 한해 접속, 서비스 요청 및 서비스 응답이 수행된 후 서로간의 접속을 끊는다.

### 3. 메시지








### 4. 네임
노드와 메시지(토픽, 서비스, 액션, 파라미터)가 가지는 고유의 식별자


### 5. 좌표 변환(TF)
각 joint들의 상대 좌표 변환
상대 좌표로 서로 연결되어 있는 각 로봇 관절의 움직임을 어떻게 모델링할 것인가?

