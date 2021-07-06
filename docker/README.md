# Problems and Solutions

1. How to solve the problem of oscillating mass for the Robot in simulation environement?

- Sol: The problem of oscillating mass is due to the virtue of the Marvin robot structure.
       And it was overcome by ncreasing the gain factor in the URDF description in the
       marvin.gazebo.xacro file in mmarvin_sim package.
       The <kp>10000000000000000000.0</kp> tag value is increased to high to prevent the robot from falling down.

       For further reference - gazebosim.answers(http://answers.gazebosim.org/question/13982/setting-contact-coefficients/)     
       
       
- The images below illustrates. 
	- Balanced mass,inertia implies that the robot performs stable movement, 
	- Unbalanced masses, inertia of robot implies that the robot performs unstable movement. Hence, the correction was introduced as explained above description.   
    - Unbalanced structure and C.G of the Robot

- Balanced Inertia       
<img src="marvin_sim_package/Balanced_Inertias.jpg" alt="drawing" width="200" />

- Un-Balanced Inertia 
<img src="marvin_sim_package/Imbalanced_Interitias_as_seen_responsible_for_Oscillation.jpg" alt="drawing" width="200" />

- Un-Balanced Inertia with Centre of Mass Highlighted
<img src="marvin_sim_package/Centre_Of_Gravity.jpg" alt="drawing" width="200" />
  
--------------------------------------------------------------------------------------------------------------------------------------------------------------



2. Is there another secondary method to implement omni directional movement for the robot ?

- Sol: Yes, there exists another method for enabling the movement of the robot similar to omni directional. 
       It is done by utilising the libgazebo_ros_control.so plugin in the URDF gazebo.macro for the mobile base robot.
       

       For further, details regarding this approach to omni directional problem. 
       ( https://bitbucket.org/theconstructcore/plannar_mover/src/master/ and http://www.theconstructsim.com/gazebo-qa-004-create-planar-moving-element-gazebo-ros/)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
       
3. How to restrict the angle of the S300 sick laser scanner ? (Because of the interference of the Laser rays with the Wheels of robot)

- Sol: 

1. Method 1 is to edit the angle in the URDF description to desired angle 90 Deg = 1.57079 radians . which is the effective angular range for operation.
       
2. Method 2 is to use the ROS Laser filter package. Which can be used to achieve the purpose of restricting the angle min and max range S300 Sick Laserscanner.
          Edit the laser_config.yaml  package peresent in marvin_bringup package. And add the parameter refering to below ros wiki weblink. 
          For further details refer (https://wiki.ros.org/laser_filters)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

4. How to increase the speed of the Mapping the environement utilising the two laser scanner readings.

- Sol: 

1. The external package was identified and utilised for the above purpose.

The concatenation of the Laser scanner readings from front sick S300 Laser scanner and Rear S300 laser scanner readings located on the same plane.

The launch file were configured from the package to obtain single `/scan` laser scanner topic which is the linear combination of Front and Rear Laser scanner readings.
