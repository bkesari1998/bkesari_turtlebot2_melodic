# turtlebot2-melodic

Instalation of turtlebot2, astra camera, and rplidar packages on ROS melodic. This repository is heavily based of the repository below:
https://github.com/gaunthan/Turtlebot2-On-Melodic

## Table of Contents
1. Installing turtlebot2 packages
2. Getting astra camera working
3. Getting RP-Lidar working
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

## Getting astra camera
