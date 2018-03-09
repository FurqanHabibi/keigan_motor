# keigan_motor

## Note
RealSense ROS wrapper version
- https://github.com/intel-ros/realsense/releases

Realsense SDK version
- https://github.com/IntelRealSense/librealsense/releases

## Install RealSense SDK
### Raspberry Pi
- https://github.com/IntelRealSense/librealsense/blob/master/doc/RaspberryPi3.md

### Remote PC
- https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md

## Dependencies
### Raspberry Pi and Remote PC
```
# clone realsense ROS module and install it's dependencies
$ mkdir -p ~/realsense_ws/src
$ cd ~/realsense_ws/src
$ git clone https://github.com/intel-ros/realsense
$ mv realsense/realsense2_camera .
$ rm -rf realsense/
$ cd ~/realsense_ws
$ rosdep install --from-paths src --ignore-src -r -y

# clone keigan_motor_driver and keigan_motor ROS modules and install it's dependencies
$ cd ~/catkin_ws/src
$ git clone https://github.com/FurqanHabibi/keigan_motor_driver
$ git clone https://github.com/FurqanHabibi/keigan_motor
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y
```

## Setup
### Raspberry Pi and Remote PC
```
$ cd ~/realsense_ws
$ catkin_make -DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
$ catkin_make install
$ source devel/setup.bash
$ cd ~/catkin_ws
$ catkin_make
$ source devel/setup.bash
```

### Raspberry Pi only
```
$ sh $(rospack find keigan_motor_bringup)/scripts/create_udev_rules.sh
```

## Usage
### Raspberry Pi
```
$ roslaunch keigan_motor_bringup keigan_motor.launch
```

### Remote PC
#### Mapping
```
$ roslaunch keigan_motor_mapping gmapping.launch
$ rosrun map_server map_saver -f $(rospack find keigan_motor_navigation)/map/<map_name>
```
#### Navigation
```
$ roslaunch keigan_motor_navigation amcl.launch map_file:=<map_name>.yaml
```
####
