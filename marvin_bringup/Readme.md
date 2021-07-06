# marvin_bring_up

**Basic Setup Tools**:

This package allows us to move Marvin around using Keyboard or Joystick.

Before using this package, make sure the following packages are installed:

[teleop_twist_keyboard] (http://wiki.ros.org/teleop_twist_keyboard): `sudo apt-get install ros-kinetic-teleop-twist-keyboard`

[teleop_twist_joy] (http://wiki.ros.org/teleop_twist_joy): `sudo apt-get install ros-kinetic-teleop-twist-joy`

[joy] (http://wiki.ros.org/joy): `sudo apt-get install ros-kinetic-joy`

**To launch the package (Gazebo Sim)**:

`roslaunch marvin_gazebo marvin_world.launch`

`roslaunch ira_laser_tools laserscan_multi_merger.launch`

After Launching the marvin_gazebo package.

**To control the robot using keyboard:**

*In simulation:* `roslaunch marvin_bringup kb_teleop.launch`

**To control the robot using joystick:**

*In simulation:* `roslaunch marvin_bringup joy_teleop.launch`

**NOTE**: 

## Keyboard Controls:

The keyboard controls are given below:


*In Command Terminal Terminal*

![teleop](https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/wikis/uploads/9c6dfba18f4e1c6af3e78e6c134e3848/teleop.png)

