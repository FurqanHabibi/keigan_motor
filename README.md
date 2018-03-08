# keigan_motor

### Dependencies
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/intel-ros/realsense
$ mv realsense/realsense2_camera .
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y
```

### Setup
```
$ cd ~/catkin_ws
$ catkin_make
$ source devel/setup.bash
$ sh $(rospack find keigan_motor_bringup)/scripts/create_udev_rules.sh
```
