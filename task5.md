# Create and Save a map by Useing Turtlebot3 with SLAM approach
-Frist of all, open turtlebot3 website in google or any browser you have and Change the vision to noetic.  
-We only need option3 and 6 called "Quick start guide" and "simulation".

-From 3.0 "quick start guide" we need :

3.1.2 Install ROS on Remote PC  
$ sudo apt update  
$ sudo apt upgrade  
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh  
$ chmod 755 ./install_ros_noetic.sh  
$ bash ./install_ros_noetic.sh 

3.1.3 Install Dependent ROS packages  
$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers

3.1.4 Install TurtleBot3 packages  
$ sudo apt install ros-noetic-dynamixel-sdk  
$ sudo apt install ros-noetic-turtlebot3-msgs  
$ sudo apt install ros-noetic-turtlebot3


-From 6.0 "simulation" we only need 6.1 "Gazebo simulation" and 6.2 "SLAM Simulation" : 

Gazebo simulation  
6.1.1 Install Simulation Package   
$ cd ~/catkin_ws/src/  
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git  
$ cd ~/catkin_ws && catkin_make

6.1.2 Launch Simulation World  
There are Three simulation environments are prepared for TurtleBot3 which are (burger,waffle,house). select one of these environments to launch Gazebo.  
As for me, I chose the waffle.  
$ export TURTLEBOT3_MODEL=waffle  
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

6.1.3 Operate TurtleBot3  
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

SLAM Simulation  
6.2.1 Launch Simulation World   
$ export TURTLEBOT3_MODEL=waffle  
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

6.2.2 Run SLAM Node   
$ export TURTLEBOT3_MODEL=waffle  
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

6.2.3 Run Teleoperation Node  
$ export TURTLEBOT3_MODEL=waffle  
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch










## Control Your TurtleBot3!

Moving around: w a s d x  
w/x : increase/decrease linear velocity  
a/d : increase/decrease angular velocity  
space key, s : force stop  
CTRL-C to quit

6.2.4 Save Map  
$ rosrun map_server map_saver -f ~/map

## the result  


![smart method](https://user-images.githubusercontent.com/112234071/187017135-5ffb1506-23e3-449a-9475-84f1ee41ff1b.PNG)
