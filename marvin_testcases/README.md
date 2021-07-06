## Test Cases for Functionalities



This package contains the Automated Test Cases for Marvin Basic Functionality Test_Cases

**To Run the Test Case Run the Server Node and Run the Test Cases**:

**Scripts**:

**1. Distance Test Case :**

To move the robot to a predefined distance and test if the movement of the robot is achieved

<rosrun test_distance.py>

`rosrun marvin_testcases test_distance.py`

After running the folllowing above script the bot moves in the simulation and Testcase Pass sucessfully


we have performed integration test, by moving the bot to a given distance by publishing velocity commands and verified the distance moved by subscribing the "gazebo model states" topic.

**2. Kinect Test :**

To spawn the model for laser and kinect testing spwan the Model which appears in front of Marvin

`rosrun gazebo_ros spawn_model -file /root/catkin_ws/src/prj-iki-robotics/ws18_raju_allampally_robot_test_sim-master/marvin_testcases/scripts/laser_test/my_sdf.sdf -sdf -model marvin_testcases`

We need to convert the Point cloud data from the RGB-Depth into `/scan` topic by running the following command

`roslaunch marvin_testcases kinect_test.launch`

To Run Test_case of Kinect_Test

`rosrun marvin_testcases test_case_kinect.py`

We have performed the unit test on kinect sensor. Intially we have used `"depthimage_to_laserscan"` topic in ROS to convert depthimage obtained from kinect sensor in to laserscan data, and performed unit test by keeping an object at a known distance and subscribed the "laserscan" topic,and verified if the object kept at known distance equal to the value obtained after subscribing "laserscan" topic.

**3. Laser Test :**

To Run Test_case of Laser Hukoyu Laser 

`rosrun marvin_testcases test_laser.py`

We have performed the unit test on Laser sensor.By keeping an object at a known distance and subscribed the "laserscan" topic,and verified if the object kept at known distance equal to the value obtained after subscribing "laserscan" topic.

**4. Linear actuator_test :**

To Start the Server of linear_actuator

`rosrun marvin_testcases linear_server.py`

To Run Test_case of linear_actuator

`rosrun marvin_testcases linear_guide_test.py`
 
we have performed the unit test on Linear actuator.Initially created action server and action client. The goal is sent from the action client file on to the server, and action server receives the goal and publishes the given goal on to the ROS topic called  "/marvin/linear_actuator_controller/command`".
We subscribed in ROS "joint states" topic and compared it with given goal values.The test is passed if linear actuator reaches the given goal value.

**5. PTU Pan_test :**

To Start the Server of PTU Panning for left and right movement(-45 and +45)

<rosrun pan_server.py>

`rosrun marvin_testcases pan_server.py`

To Run Test_case of pan_test

`rosrun marvin_testcases test_pan.py`

we have performed the unit test on PTU while panning.Initially created action server and action client. The goal is sent from the action client file on to the server, and action server receives the goal and publishes the given goal on to the ROS topic called  "/marvin/ptu_pan_controller/command`".
We subscribed in ROS "joint states" topic and compared it with given goal values.The test is passed if PTU while panning  reaches the given goal value.

**6. PTU Tilt test :**

To Start the Server of PTU tilt for Up and Down movement(-45 and +45)

`rosrun marvin_testcases tilt_server.py`

To Run Test_case of pan_test

`rosrun marvin_testcases test_tilt.py`

we have performed the unit test on PTU while tilting.Initially created action server and action client. The goal is sent from the action client file on to the server, and action server receives the goal and publishes the given goal on to the ROS topic called  "`/marvin/ptu_tilt_controller/command``".
We subscribed in ROS "joint states" topic and compared it with given goal values.The test is passed if PTU while tilting reaches the given goal value.

<img src="https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/wikis/uploads/21ce78af14f4cc230cbdf955960e4d34/Only_KinectTest.jpg" alt="drawing" width="300" />

<img src="https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/wikis/uploads/e7a87a120ff0d07468800fab25e02b7a/kinect_with_linearGuide_testing.jpg" alt="drawing" width="500" />