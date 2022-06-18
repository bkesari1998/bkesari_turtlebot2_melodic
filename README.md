# turtlebot2-melodic

Instalation of turtlebot2, astra camera, and rplidar packages on ROS melodic

## Table of Contents
1. Installing turtlebot2 packages
2. Installing Astra camera packages
3. Installing RP-Lidar packages
4. Creating a map
5. Autonomous navigation of a known map
6. Sources

## Installing turtlebot2 packages
Create or `cd` into a catkin workspace

```
mkdir -p catkin_ws/src
cd catkin_ws
catkin_make
```

Run the command below within the root of the catkin workspace:
```
curl -sLf https://raw.githubusercontent.com/bkesari1998/bkesari1998-tbot2-melodic-install/master/install_basic.sh | bash
```
Install the following dependencies:
```
sudo apt-get install ros-melodic-move-base*
sudo apt-get install ros-melodic-map-server*
sudo apt-get install ros-melodic-amcl*
sudo apt-get install ros-melodic-navigation*
```

Build the workspace:
```
catkin_make
```

## Installing Astra camera packages
Install dependences
```
sudo apt install ros-melodic-rgbd-launch ros-melodic-libuvc ros-melodic-libuvc-camera ros-melodic-libuvc-ros
```

Clone the repository into your ROS workspace:
```
cd ~/catkin_ws/src
git clone https://github.com/bkesari/bkesari_ros_astra_camera
```

Create astra udev rule
```
roscd astra_camera
chmod 777 /scripts/create_udev_rules
./scripts/create_udev_rules
```

Go to catkin workspace and compile astra_camera
```
cd ~/catkin_ws
catkin_make --pkg astra_camera
```

## Installing RP-Lidar packages

Clone the repository into your ROS workspace:
```
cd ~/catkin_ws/src
https://github.com/bkesari1998/bkesari_rplidar_ros.git
```

Build the workspace:
```
cd ~/catkin_ws
catkin_make
```

If the 
