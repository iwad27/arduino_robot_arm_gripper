# arduino_robot_arm_gripper
ROS packages that can be used to plan and execute motion trajectories for a robot arm in simulation and real-life.



These packages were tested under ROS kinetic and Ubuntu 16.04

The robot arm uses Moveit plugin to apply kinematics by the KDL solver. These packages can be tested in the gazebo simulation tool and the real robot arm, where the ROS system and Arduino code share the ```/joint_states``` topic to control motors.


## Dependencies
run this instruction inside your workspace:

```$ rosdep install --from-paths src --ignore-src -r -y```

make sure you installed all these packages:
```
$ sudo apt-get install ros-kinetic-moveit
$ sudo apt-get install ros-kinetic-joint-state-publisher ros-kinetic-joint-state-publisher-gui
$ sudo apt-get install ros-kinetic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-ros-control

```


## Robot Arm
The robot arm has 5 joints, 4 joints to connect the arm links and the last joint for the gripper.
### Circuit diagram 
![circuit](circuit.png)
### Robot initial positions
![positions](positions.png)

## Usage
### Controlling the robot arm by joint_state_publisher
```$ roslaunch arm_pkg check_motors.launch```

You can also connect with hardware by running:

```$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200```

(Note: You may need to use ttyACM)

#### Simulation
Run the following instructions to use gazebo
```
$ roslaunch arm_pkg check_motors.launch
$ roslaunch arm_pkg check_motors_gazebo.launch
$ rosrun arm_pkg joint_states_to_gazebo.py
```

### Controlling the robot arm by Moveit and kinematics
```$ roslaunch moveit_config_pkg demo.launch```

You can also connect with hardware by running:

```$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200```

(Note: You may need to use ttyACM)

#### Simulation
Run the following instruction to use gazebo

```$ roslaunch moveit_config_pkg demo_gazebo.launch```
