# ch3. ROS 개발환경 구축
## ROS 한줄 설치
<$wget gttps://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh>  

## ROS 수동 설치
* ros 설치 : http://wiki.ros.org/noetic/Installation   
* ros 환경설정 : http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment
* 자세한 설명은 https://m.blog.naver.com/PostView.naver?blogId=yoouungg&logNo=223004567994&isFromSearchAddView=true 를 참고.

## ROS 환경설정
<img src="https://github.com/riseacademy/ROS-Study/assets/101642425/bba184dd-41b9-493b-8020-b1c9e9da6d3c" width="70%" heigh="50%" title="px(픽셀) 크기 설정" alt="rprogrammingules"></img>   
* alias는 별칭이라는 뜻으로, Linux에서 사용자가 명령어를 다른 이름으로 바꿔 사용할 수 있는 shell 내부 명령어.   
* ROS에서 자주 사용하는 긴 명령어들을 eb, sb등의 별칭으로 등록해놓음. (단축키 같은 느낌)

## ROS 동작테스트
~~~c
$ rosrun turtlesim turtlesim_node
~~~
* Terminal 창을 새로 연 후 위 명령어 실행 -> turtlesim node 실행   
* turtlesim은 ros_tutorials repository 하위에 속해있는 ROS tutorial package로, ROS를 처음 접하는 사용자들에게 tutorial을 제공하기 위해 제작된 학습용 package

~~~c
$ rosrun turtlesim turtle_teleop_key
~~~
* teleop 실행 후 노트북의 'W A S D X' 키들을 입력하여 거북이를 움직임  

      
<img src="https://github.com/riseacademy/ROS-Study/assets/101642425/c51cf91e-0efa-4ad4-9e7c-480091c10f41)" width="70%" heigh="50%" title="px(픽셀) 크기 설정" alt="rprogrammingules"></img>
