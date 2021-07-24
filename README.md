# Demo of Prius in ROS/GAZEBO

This is a simulation of a Prius in [gazebo 9](http://gazebosim.org) with sensor data being published using [ROS kinetic](http://wiki.ros.org/kinetic/Installation)
The car's throttle, brake, steering, and gear shifting are controlled by publishing a ROS message.
A ROS node allows driving with a gamepad or joystick.

# Video + Pictures

A video and screenshots of the demo can be seen in this blog post: https://www.osrfoundation.org/simulated-car-demo/

![Prius Image](https://www.osrfoundation.org/wordpress2/wp-content/uploads/2017/06/prius_roundabout_exit.png)

# Requirements

This demo has been tested on Ubuntu Xenial (16.04)

* An X server
* [Docker](https://www.docker.com/get-docker)
* [nvidia-docker2](https://github.com/nvidia/nvidia-docker/wiki/Installation-(version-2.0))
* The current user is a member of the docker group or other group with docker execution rights.
* [rocker](https://github.com/osrf/rocker)

# Recommended

* A joystick
* A joystick driver which creates links to `/dev/input/js0` or `/dev/input/js1`

This has been tested with the Logitech F710 in Xbox mode. If you have a different joystick you may need to adjust the parameters for the very basic joystick_translator node: https://github.com/osrf/car_demo/blob/master/car_demo/nodes/joystick_translator

# Building

First clone the repo, then run the script `build_demo.bash`.
It builds a docker image with the local source code inside.

```
$ cd car_demo
$ ./build_demo.bash
```

# Running

Connect a game controller to your PC.
Use the script `run_demo.bash` to run the demo.

```
$ ./run_demo.bash
```
An [RVIZ](http://wiki.ros.org/rviz) window will open showing the car and sensor output.
A gazebo window will appear showing the simulation.
Either use the controller to drive the prius around the world, or click on the gazebo window and use the `WASD` keys to drive the car.

If using a Logitech F710 controller:

* Make sure the MODE status light is off
* Set the swtich to XInput mode
* The right stick controls throttle and brake
* The left stick controls steering
* Y puts the car into DRIVE
* A puts the car into REVERSE
* B puts the car into NEUTRAL


### Prius joint list
1. base_link_connection,        type=fixed
2. steering_joint,              type=continuous
3. front_left_steer_joint,      type=continuous
4. front_right_steer_joint,     type=continuous
5. front_left_wheel_joint,      type=continuous
6. front_right_wheel_joint,     type=continuous
7. rear_left_wheel_joint,       type=continuous
8. rear_right_wheel_joint,      type=continuous

9. center_laser_joint,          type=fixed
10. front_left_laser_joint,      type=fixed
11. front_right_laser_joint,     type=fixed

12. front_camera_joint,         type=fixed
13. front_camera_optical_joint, type=fixed
14. back_camera_joint,          type=fixed
15. back_camera_optical_joint,  type=fixed
16. left_camera_joint,          type=fixed
17. left_camera_optical_joint,  type=fixed
18. right_camera_joint,         type=fixed
19. right_camera_optical_joint, type=fixed

20. back_left_far_sonar_joint,      type=fixed
21. back_left_middle_sonar_joint,   type=fixed
22. back_right_far_sonar_joint,     type=fixed
23. back_right_middle_sonar_joint,  type=fixed

24. front_left_far_sonar_joint,      type=fixed
25. front_left_middle_sonar_joint,   type=fixed
26. front_right_far_sonar_joint,     type=fixed
27. front_right_middle_sonar_joint,  type=fixed
