# Robot_Controller (ROS 2 Jazzy)

A ROS 2 Jazzy Python package implementing a simple differential drive controller for a mobile robot. The node subscribes to `/cmd_vel`, converts linear and angular velocity into wheel velocities, and publishes wheel commands for a ROS 2 control-based robot in Gazebo simulation.

---

## Features

- Differential drive kinematics implementation
- Subscribes to `/cmd_vel` (`geometry_msgs/msg/TwistStamped`)
- Publishes wheel commands using `Float64MultiArray`
- Works with Gazebo simulation and ros2_control
- Uses wheel radius and wheel separation for motion conversion

---

## Robot Controller Node

### SimpleController

This node performs the following:

- Subscribes to `/cmd_vel`
- Extracts:
  - Linear velocity (x)
  - Angular velocity (z)
- Converts robot velocity into wheel velocities using differential drive equations
- Publishes wheel velocities to:
  - `simple_velocity_controller/commands`

---

## Topics

### Subscribed Topics

- `/cmd_vel`
  - Type: `geometry_msgs/msg/TwistStamped`
  - Description: Velocity commands for the robot

### Published Topics

- `simple_velocity_controller/commands`
  - Type: `std_msgs/msg/Float64MultiArray`
  - Description: Left and right wheel velocity commands

---

## Terminal Commands

Here are your **terminal-wise CLI commands**:

---

### Terminal 1 — Build workspace

```bash 
cd ~/robot_ws
colcon build
```

---

### Terminal 2 — Launch Gazebo simulation

```bash 
. install/setup.bash
ros2 launch robot_description gazebo.launch.py
```

---

### Terminal 3 — Launch controller

```bash 
. install/setup.bash
ros2 launch robot_controller controller.launch.py
```

---

### Terminal 4 — Send velocity command

```bash 
. install/setup.bash
ros2 topic pub /cmd_vel geometry_msgs/msg/TwistStamped "{twist: {linear: {x: 0.5}, angular: {z: 0.5}}}"
```


## Conclusion

This project implements a simple yet effective differential drive controller in ROS 2 Jazzy, connecting robot kinematics with real-time simulation in Gazebo. It demonstrates how velocity commands from `/cmd_vel` can be transformed into wheel-level control using basic mathematical models.

The setup provides a solid foundation for understanding mobile robot control systems and can be extended toward more advanced topics such as autonomous navigation, SLAM, and path planning.
