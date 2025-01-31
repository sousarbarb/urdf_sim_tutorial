# urdf_sim_tutorial

## Nonfunctional gazebo interface

```shell
roslaunch urdf_sim_tutorial gazebo.launch
```

## Gazebo plugin

1. Link Gazebo and ROS
   - See [09-publishjoints.urdf.xacro](urdf/09-publishjoints.urdf.xacro) file
```xml
  <gazebo>
    <plugin name="gazebo_ros_control" filename="libgazebo_ros_control.so">
      <robotNamespace>/</robotNamespace>
    </plugin>
  </gazebo>
```
2. Test the model that links ROS and Gazebo
   - Does not do anything. It is required more information!
```shell
roslaunch urdf_sim_tutorial gazebo.launch model:=`rospack find urdf_sim_tutorial`/urdf/09-publishjoints.urdf.xacro
```
3. Spawning controllers
   - Kind off bits of ROS code to run within Gazebo
   - Specified in the file [joints.yaml](config/joints.yaml)
4. Test the spawner script that loads the controller and publishes the state 
   of the robot's joints into ROS directly from Gazebo
   - If you execute `rostopic list`, you can see that `/joint_states` topic 
     is publishing but with nothing in it
```shell
roslaunch urdf_sim_tutorial 09-joints.launch
```
5. Transmissions
   - **For every non-fixedd joint, it is necessary to specify a transmission
     to tell Gazebo that to do with the joint!**
   - See tags `<transmission>` in the urdf file (including for the wheels)
6. Joint control
   - Specify a joint controller for each joint
   - See the yaml files in [config](config/)

## Drive the Droid

```shell
roslaunch urdf_sim_tutorial 13-diffdrive.launch
```

## Useful links to learn more about Gazebo and URDF/Xacro

- Introduction to Xacro and URDF: https://ni.www.techfak.uni-bielefeld.
  de/files/URDF-XACRO.pdf
- Tutorial URDF: http://wiki.ros.org/urdf/Tutorials
  - Using URDF in Gazebo: http://wiki.ros.org/urdf/Tutorials/Using%20a%20URDF%20in%20Gazebo
  - GitHub: https://github.com/ros/urdf_sim_tutorial/blob/master/config/diffdrive.yaml
  - Gazebo: http://gazebosim.org/tutorials/?tut=ros_urdf
