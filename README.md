# UAV SIMULATOR WITH PX4, GAZEBO SIM 8, QGROUNDCONTROL AND ROS2 HUMBLE
Instruct full guide how to download and take off drone with PX4, Gazebo Sim 8, QGroundControl and ROS2 Humble

## Table of Contents

- [INTRODUCTION](#introduction)
- [DOWNLOADS](#downloads)
  - [1. PX4-AutoPilot](#1-px4-autopilot-1)
  - [2. ROS2 Humble](#2-ros2-humble-1)
  - [3. Micro-XRCE-DDS Agent](#3-micro-xrce-dds-agent-1)
  - [4. QGroundControl](#4-qgroundcontrol-1)
- [TAKE OFF UAV](#take-off-uav)
- [CREDITS AND REFERENCES](#credits-and-references)
- [THANKS TO](#thanks-to)

## INTRODUCTION
A full turtorial step-by-step how to download, setup and run a development environment for UAV involves several software systems. Through this project, you can simulate a autonomous drones and develop your own project by yourself. Understanding comprehensively the role of each component, how they operate, interact. 

PX4-AutoPilot is a open-source flight controller software for drones. ROS2 Humble is a tool for programming robot. Gazebo Simulator is a 3D robotics simulator providing realistic enviroment for flying drones. Micro-XRCE-DDS Brigde is a communication link between PX4 and ROS2 Humble, translating and transporting messages from ROS2 to PX4 and come back. 

Beginning with realistics enviroment created by Gazebo Simulator, drone appears, controlled by PX4 and QGroundControl. Then ROS2 run the program of take off the drone. Micro-XRCE-DDS Brigde brings and translates to PX4's language. Finally PX4 control and drone flys in Gazebo Sim.


## DOWNLOADS
### 1. PX4-AutoPilot
Open your terminal, update and upgrade prepare for next step
```bash
sudo apt update
sudo apt upgrade
````
Download Git
```bash
sudo apt install git
```
Clone the PX4-Autopilot repositoryhttps://ali.khorshidi.net/ros2-px4/
```bash
git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```
Run Ubuntu set up script
```bash
bash./PX4-Autopilot/Tools/setup/ubuntu.sh
```
Reboot the system
```bash
reboot
```

### 2. ROS2 Humble

### 3. Micro-XRCE-DDS Agent
Install Agent Dependencies
```bash
pip3 install --user -U empy pyros-genmsg setuptools
```
Manual complilation
```bash
git clone https://github.com/eProsima/Micro-XRCE-DDS-Agent.git
cd Micro-XRCE-DDS-Agent
mkdir build
cd build
cmake..
make
sudo make install
sudo ldconfig /usr/local/lib/
```

### 4. QGroundControl
Download QGroundControl 4.4.5 at here [Link](https://github.com/mavlink/qgroundcontrol/releases/tag/v4.4.5)

Go to the directory where QGroundControl was downloaded (usually at :/Downloads) and make QGroundControl.AppImage executable
```bash
chmod +x ./QGroundControl.AppImage
```
Run QGroundControl 
```bash
./QGroundControl.AppImage
```

## TAKE OFF UAV
Running 4 terminal simultaneously follow this instructions:
### PX4-AutoPilot
1. Navigate to the PX4-Autopilot directory:
```bash
cd ~/Auto-Pilot
```
2. Build, run the simulation and create a drone:
```bash
make px4_sitl gz_x500
```

### QGroundControl
1. Navigate to the QGroundControl directory:
```bash
cd ~/Downloads
```
2. Run QGroundControl:
```bash
./QGroundControl
```

### Micro-XRCE-DDS Agent
1. Launch the Micro-XRCE-DDS Agent:
```bash
MicroXRCEAgent udp4 -p 8888
```

### ROS2 Humble
1. Navigate to the ROS2 Humble workspace and source the "local_setup.bash" file:
```bash
cd ~/ros2_ws
source install/setup.bash
```
2. Run the program to take off the drone
```bash
ros2 run px4_ros_com offboard_control
```

## CREDITS AND REFERENCES
This project is based on:

[Gazebo-PX4-Setup-Guide](https://github.com/MrStealYoCurls/Gazebo-PX4-Setup-Guide.git)

[Comprehensive Guide to PX4 SITL Simulation with ROS 2 and Gazebo on Ubuntu 22.04](https://ali.khorshidi.net/ros2-px4/)


## THANKS TO
[Embedded Networking Labrotatory](https://www.facebook.com/lab411)
