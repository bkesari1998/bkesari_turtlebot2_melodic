# turtlebot2-melodic

Instalation of turtlebot2, astra camera, and rplidar packages on ROS melodic

## Table of Contents
1. Installing turtlebot2 packages
2. Installing Astra camera packages
3. Installing RP-Lidar packages

## Installing turtlebot2 packages
Create or `cd` into a catkin workspace

```
mkdir -p catkin_ws/src
cd catkin_ws
catkin_make
```

Run the command below within the root of the catkin workspace:
```
curl -sLf https://raw.githubusercontent.com/bkesari1998/bkesari_turtlebot_melodic_setup/master/install_all.sh | bash
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
https://github.com/Slamtec/rplidar_ros.git
```

Build the workspace:
```
cd ~/catkin_ws
catkin_make
```

If the USB to UART Bridge driver for the device has not been installed on the computer, download the Linux 3.x.x/4.x.x/5.x.x VCP Driver from
https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers. Then, follow the directions at https://samliu.github.io/2018/01/06/rplidar-a2.html. The steps are summarized below.

1. Extract the tarball
2. run `make`
3. run `cp cp210x.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial`
4. run `insmod /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko`
5. run `insmod cp210x.ko`

To check which USB port the device is plugged into, run `ls /dev | grep ttyUSB`. The device should be plugged into USB0.
run `sudo chmod 666 /dev/ttyUSB0`
