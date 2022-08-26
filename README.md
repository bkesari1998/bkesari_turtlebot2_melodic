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
source devel/setup.bash
```

Run the command below within the root of the catkin workspace:
```
curl -sLf https://raw.githubusercontent.com/bkesari1998/bkesari_turtlebot2_melodic_setup/master/install_all.sh | bash
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
source devel/setup.bash
```

## Installing Astra camera packages
Follow the README for the astra camera package (https://github.com/orbbec/ros_astra_camera)

To use turtlebot_3dsensor.launch from the turtlebot_bringup package, set the environment variable TURTLEBOT_3D_SENSOR to astra.

## Installing RP-Lidar packages

Clone the repository into your ROS workspace:
```
cd ~/catkin_ws/src
git clone https://github.com/Slamtec/rplidar_ros.git
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
3. run `cp cp210x.ko /lib/modules/\`uname -r\`/kernel/drivers/usb/serial`
4. run `insmod /lib/modules/\`uname -r\`/kernel/drivers/usb/serial/usbserial.ko`
5. run `insmod cp210x.ko`

If the make command fails, download the patched driver from this message thread:
https://community.silabs.com/s/question/0D58Y00008u8b0SSAQ/cp210x-to-vcp-driver-failed-to-build-for-kernel-513-ubuntu-2004?language=en_US

To check which USB port the device is plugged into, run `ls /dev | grep ttyUSB`. The device should be plugged into USB0.
run `sudo chmod 666 /dev/ttyUSB0`
