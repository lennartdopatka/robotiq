# Installation

Install the repository manually or through wstool
```
wstool init ~/catkin_ws/src/
wstool merge -t ~/catkin_ws/src/ ~/catkin_ws/src/<path>/<component>.rosinstall.kinetic
wstool update -t ~/catkin_ws/src/
```
```
sudo usermod -a -G dialout $USER
reboot (or logout)
sudo apt-get install ros-kinetik-soem
cd ~/catkin_ws/src
export ROS_PACKAGE_PATH=~/catkin_ws/src:$ROS_PACKAGE_PATH
rosdep install -a -y --ignore-src
catkin_make
```
## Problems to be tested

- soem is not automatically installed from rosdep, at least in Kinetik and must be manually installed

# Running
```
rosrun robotiq_c_model_control CModelRtuNode.py /dev/ttyUSB0
```
The driver needs initializing. Example:
```
	pub = rospy.Publisher('/CModelRobotOutput', CModel_robot_output, queue_size=10)
	
	command = CModel_robot_output()
	command2 = CModel_robot_output()

	command.rACT = 0
	command.rGTO = 0
	command.rATR = 0
	command.rPR = 0
	command.rSP = 0
	command.rFR = 0

	command2.rACT = 1
	command2.rGTO = 1
	command2.rATR = 0
	command2.rPR = 0
	command2.rSP = 255
	command2.rFR = 150

	pub.publish(command)
	rospy.sleep(2)
	pub.publish(command2)
	rospy.sleep(2)
```

# Robotiq

[ROS-Industrial][] robotiq meta-package.  See the [ROS wiki][] page for more information.  

## Contents

This repo holds source code for all versions > groovy. For those versions <= groovy see: [SVN repo][]

[ROS-Industrial]: http://www.ros.org/wiki/Industrial
[ROS wiki]: http://ros.org/wiki/robotiq
[SVN repo]: https://code.google.com/p/swri-ros-pkg/source/browse

