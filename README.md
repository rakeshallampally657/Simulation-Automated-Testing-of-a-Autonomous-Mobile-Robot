# Automated_Testing

- Repository for Updated Marvin With Omni_Directional and Moveit and SLAM Navigation Package

- Enabling Omni Directional Movement of Robot and Teleoperating the Robot

- Moveit configuration of Robot Arm
 
- Testing Basic Robot Functinalities Robot with (Rostest,Unitest,Python)

- SLAM Implementation (Simultaneous Localisation and Mapping)

## Getting started
- Build the docker container and start it with the docker-compose.yaml with simulation run below commands
- `docker-compose -f docker-compose.yml up`
- In new Terminal command `docker exec -it docker_iki-robot-sim_1 bash` will enable us with an interactive bash shell on the container .
- Need to Install external Dependencies (could not be included in docker_compose)
- `sudo apt-get install ros-kinetic-turtlebot-simulator ros-kinetic-turtlebot-teleop`
- `sudo apt-get dist-upgrade`
- `sudo apt-get update`
- `sudo apt-get upgrade`
- To launch Robot in simulation `roslaunch marvin_gazebo marvin_world.launch`
- To enable `/scan/multi` laser scan topic `roslaunch ira_laser_tools laserscan_multi_merger.launch` (recomended in new shell)
- Detailed Explanation marvin simulation docker (https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/wikis/Marvin-Simulation-in-Docker-Container)
- Individual Modules Description (https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/wikis/home) 

## External dependencies
Dependencies for Docker :

1. ROS Navigation - (https://github.com/ros-planning/navigation)
2. Ira Laser Tools - (https://github.com/iralabdisco/ira_laser_tools) - Modified the package launch files.


## Authors
- Rakesh Allampally - Main Contributor - @ra-171967


## License
To be determined.

## Problems and solutions 
Refer the below links for further detailed description.
(https://fbe-gitlab.hs-weingarten.de/stud-iki/prj-master/ws18_raju_allampally_robot_test_sim/blob/master/docker/README.md)

