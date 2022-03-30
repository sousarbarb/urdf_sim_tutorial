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
2. Launch the model that links ROS and Gazebo
   - Does not do anything. It is required more information!
```shell
roslaunch urdf_sim_tutorial gazebo.launch model:=`rospack find urdf_sim_tutorial`/urdf/09-publishjoints.urdf.xacro
```
