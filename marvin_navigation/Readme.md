# marvin_navigation

**Basic Setup Navigation:**

This is the mega package that launches the modules configured for Marvins's navigation. Before using this package,
the following packages must be installed:

[gmapping] (http://wiki.ros.org/gmapping): `sudo apt-get install ros-kinetic-gmapping`

[map_server] (http://wiki.ros.org/map_server): `sudo apt-get install ros-kinetic-map-server`

[amcl] (http://wiki.ros.org/amcl): `sudo apt-get install ros-kinetic-amcl`

[move_base] (http://wiki.ros.org/move_base): `sudo apt-get install ros-kinetic-move-base`

*********************************************************************************************************

**To map a room (launches preconfigured Rviz):**

*In simulation:*  `roslaunch marvin_navigation gmapping_sim.launch`

**To move robot to simple goals defined by 2D_Nav_goal(launches preconfigured Rviz):**

*In simulation:* `roslaunch marvin_navigation gmapping_sim.launch`

On Sucessfully Launching the gmapping package configured.

![RVIZ_gmapping](https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/wikis/uploads/dd2b0c46e4e0d268f2e8449df1c3e74c/RVIZ_gmapping.png)

Once you create a map, you need to save it if you want to use it later, using:

`rosrun map_server map_saver -f name.yaml`

Here standard maps can be used playground.yaml (other Maps iki_lab.yaml, iki_arena.yaml)

**To localise the robot (launches preconfigured Rviz):**

*In simulation:* `roslaunch marvin_navigation amcl_sim.launch`

**To launch autonomous navigation of the robot (launches preconfigured Rviz):**

*In simulation:* `roslaunch marvin_navigation move_base_sim.launch`

The default map file is the `playground.yaml` file stored in this package.

## move_base Parameters

This package currently implements the TrajectoryPlannerROS (http://wiki.ros.org/base_local_planner) as the local planner for the navigation.
All parameters (which are mostly unchanged from the navigation tutorials) are stored in the `params` directory.

On Sucessfully Launching the marvin_navigation move_base.The Robot is Ready for navigating to Simple Goals.


![move_base_and_Simulation](https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/wikis/uploads/705186ff1ece81977d88c68240a4e9c1/move_base_and_Simulation.png)

# Steps Involved in Configuring the Marvin Navigation Stack 

**Generating Map**

**Localise the Robot in environement**:

We should localize the bot, to tell where it is located exactly in the map

**Publishing the Goal to RVIZ**:

Then we send goal, by clicking 2D Nav-goal in rviz

**1) Generating Map:**

Map is created using Gmapping package in ROS. Map is generated with the help of Laser and pose data that is provided by the robot and by moving around the environment. ROS-SLAM gmapping node basically generates Occupancy grid map of the environment.

• Initially launch file started with slam_gmapping_node. Then we teleop robot in the environment.

• So gmapping node subscribed the `/scan/multi` laser topic and tf , in order to get the data it needed and built the map.

• The generated map is published on to the `/map_topic` , so that we can visualize map in rviz.
Map topic used messages of type `nav_msgs/occupancygrid`. 
In OGM `0` indicates completely free, `100` indicates completely occupied& `-1` for unknown.

We are Save the map : By using below command.

rosrun map_server map_saver –f <name_of_the_map>		

Thus maps data saved in 2 files . One is (.yaml) file which contains map meta data such as image name,range ,resolution etc .and other is (.pgm) file.

Loading the map: we load the saved map with following command in the launch file:

`<rosparam file="$(find marvin_navigation)/config/gmapping.yaml" command="load" />`

**Theory Behind Map Generation :**

TF: when object placed at distance 3 .It is considered as at distance 3 from the sensor, but not from a robot. So we perform the transformation from the sensor to the robot to calculate the distance of the object from the robot. 
Command to view tf frames:

rosrun tf view_frames 

For slam gmapping we perform 2 transforms:
1) Laser to Baselink
2) Baselink to Odom

*************************************************************************************************************

**2) Localisation:**

a) Add Laserscan and map & poseArray to see the positon of robot in rviz.

b) Click 2D pose in rviz, so that it localises as same position and orientation as seen in simulation.
It uses monte carlo localisation.

**Theory Behind Localisation:**

**Monte Carlo Localization or particle Localitation:** 

Robot does always moves as expected. It generates many guesses where the robot is going to move. These guesses are known as particle. Each particle contains the description of the future possible pose .When the robot observes the environment via sensor readings it discards the particles don’t match with readings and generate particles that look more close and most probable pose the robot is in. “so more you move the robot more data you get from sensors and more precise the localization is”

We used Amcl (adaptive monte carlo localization) node in ROS to localize the robot. It subscribes the laser topic and transformations of robot and publishes its estimated position on the map.

Command in launch file:

`<node pkg="amcl" type="amcl" name="amcl">`


TF: we should ensure the transformation tree from laser to odom.

**Parameters declared in amcl launch file:**

Odom_model_type : type of odom . eg: diff,omni,corrected-omni

Odom_frame_id: frame associated with Odom

Base_frame_id: frame associated with robot base  eg:baselink

• Filter parameters are saved in amcl.yaml file and loaded in amcl launch file.


