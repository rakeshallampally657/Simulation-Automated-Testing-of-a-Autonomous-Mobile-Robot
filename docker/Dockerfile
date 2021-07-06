ARG DOCKER_BASE_IMAGE=141.69.58.19:5000/iki/marvin:kinetic
FROM $DOCKER_BASE_IMAGE
MAINTAINER ra-171967@hs-weingarten.de

#install dependencies
RUN apt-key del 421C365BD9FF1F717815A3895523BAEEB01FA116 && \
    apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 && \
    apt-get update && apt-get -y install \
    ros-kinetic-moveit \
    ros-kinetic-controller*



#clone repos:
COPY . /root/catkin_ws/src/prj-iki-robotics/ws18_raju_allampally_robot_test_sim-master
