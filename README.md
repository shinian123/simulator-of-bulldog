ork with kinect1 and bulldog simulator
### Installation
First build your workplace:
```bash
        mkdir bulldog_simulator_ws/src && cd bulldog_simulator_ws/src
```
Then download the pipeline:
```bash
        git clone https://github.com/shinian123/simulator-of-bulldog.git
```
Make:
```bash
        cd ..
        catkin_make
        sudo chmod -R 777 *
```
## Quick Guide
### Step 1: Load the robot in gazebo:
```bash
        roslaunch bulldog_gazebo bulldog_empty_world.launch world_name:=/home/
        cheng/catkin_gazebo/src/bulldog_simulator/bulldog_gazebo/box.world
```
### Step 2: Enable the arms and grippers:
```bash
        roslaunch bulldog_gazebo_moveit_config bulldog_gazebo_moveit_execution.launch
```
```
If arms and grippers are safely enabled, those four drivers can be correctly loaded.
### Step 3 : Run the pick and place demo
* Open a new terminal, run the gripper listener :
```bash
        rosrun seven_dof_arm_test double_gripper_gazebo.py
```
* Open another terminal, run the object recognition program :
```bash
        rosrun object_recognition_core detection -c  \
        `rospack find object_recognition_linemod`/conf/detection_gazebo.ros.ork
```
* Run Rviz :  
`rviz `   
When the rviz is loaded, add a new panel named  `rviz_bulldog_commander`,
which looks like below: 
* Login bulldog and run the grasp_demo:
```bash
        ssh bulldog@192.168.1.30
        rosrun seven_dof_arm_test grasp_demo_gazebo
```
All programs are loaded, now you can use the rviz plugin to implement the whole process.
