# 🤖 CSE412 Robotics Course — Assignment 2  
### *Build Your Own Robot (Diff Drive + Camera + TF + Ball Chaser)*

**Student:** Göktürk Can  
**Student No:** 230611501  
**Instructor:** Asst. Prof. Dr. Abdurrahman Bayrak  
**University:** Istanbul Health and Technology University  
**Department:** Computer / Software Engineering  
**Semester:** Fall 2025  
**Programming Language:** Python  
**ROS2 Distribution:** Humble  
**Simulator:** Gazebo Harmonic  

---

## 🧭 Objective

This project implements a **differential-drive mobile robot** in **Gazebo Harmonic**, controlled via **ROS2 Humble**, equipped with a **camera** and a **Ball Chaser node** written in Python that follows a white ball visible in the camera feed.  
All subsystems are integrated into a **single launch file** for streamlined execution.

---

## 🧩 Project Overview

### **System Components**
- **Robot Model:** chassis, left/right wheels, caster wheel, camera link  
- **TF Tree:** `world → odom → base_link → (left/right/caster)_link → camera_link`  
- **Motion Control:** `gazebo_ros_diff_drive` plugin  
- **Camera:** Gazebo camera bridged to `/camera/image_raw`  
- **Ball Chaser Node:** subscribes to camera feed, publishes `/cmd_vel` commands  

---

## 📁 Project Structure

~/ros2_ws/
└── src/
└── my_robot_project/
├── my_robot_description/
│ ├── urdf/my_robot.urdf.xacro
│ ├── meshes/
│ ├── launch/display.launch.py
│ ├── package.xml
│ └── CMakeLists.txt
├── my_robot_gazebo/
│ ├── worlds/ball_world.sdf
│ ├── launch/gazebo.launch.py
│ ├── package.xml
│ └── CMakeLists.txt
├── my_robot_bringup/
│ ├── launch/bringup.launch.py
│ ├── package.xml
│ └── CMakeLists.txt
└── ball_chaser/
├── ball_chaser/ball_chaser_node.py
├── setup.py
├── setup.cfg
├── package.xml
└── resource/ball_chaser


---

## ⚙️ Installation and Setup

### 1️⃣ Prerequisites & Workspace Setup

```bash
# Update and install dependencies
sudo apt update
sudo apt install ros-humble-desktop
sudo apt install gz-harmonic ros-humble-gazebo-ros-pkgs
sudo apt install ros-humble-cv-bridge python3-opencv

# Create workspace and source folder
cd ~
mkdir -p ros2_ws/src
cd ros2_ws/src

# Create project packages
ros2 pkg create my_robot_description --build-type ament_cmake
ros2 pkg create my_robot_gazebo --build-type ament_cmake
ros2 pkg create my_robot_bringup --build-type ament_cmake
ros2 pkg create ball_chaser --build-type ament_python --dependencies rclpy sensor_msgs geometry_msgs cv_bridge

# Build the workspace
cd ~/ros2_ws
colcon build
source install/setup.bash

## 🎥 Demonstration Video

▶️ **YouTube (Unlisted):** [https://youtu.be/lx7NfIekOpU](https://youtu.be/lx7NfIekOpU)

### **Shown in the Video**
- 🎬 Running `ssf.sh` (face visible)  
- 🚀 Launching `bringup.launch.py`  
- 🌍 Gazebo simulation (robot + white ball)  
- 🛰️ RViz TF and camera image view  
- 🤖 Robot follows the white ball and stops when lost  

---

## 📄 PDF Report Summary (`A2_230611501_GoktürkCan.pdf`)

> IEEE-style formatted, aligned with instructor’s rubric.

---

### **1. System Information**
Ubuntu 22.04 LTS, ROS2 Humble, Gazebo Harmonic, Python 3.10, OpenCV 4.8.0  
Hardware: MSI Katana A15 (Ryzen 9 8945HS, RTX 4070, 32 GB RAM)

---

### **2. SSF Output**
Command:
```bash
bash ssf.sh



### **3. Robot Model and URDF**
```bash
URDF: my_robot_description/urdf/my_robot.urdf.xacro
Links: base_link, left/right wheel, caster, camera
TF Chain: world → odom → base_link → wheels → camera_link
Verified via display.launch.py in RViz.


### **4. Diff Drive Integration**
```bash
Plugin: gazebo_ros_diff_drive
Parameters: wheel_separation = 0.3, wheel_radius = 0.05
Topic: /cmd_vel
✅ Robot executed linear and angular motion correctly.

###**5. Camera and RViz Verification**
```bash
Camera publishes /camera/image_raw
TF structure verified via:


###**6. Ball Chaser Node (Python)**

File: ball_chaser/ball_chaser/ball_chaser_node.py
Input: /camera/image_raw  Output: /cmd_vel

Algorithm Steps:

Convert image to HSV color space
Extract white mask
Determine centroid position
Publish velocity based on position


###**7. Experiments and Results**

🟢 Ball center → forward motion

🔵 Ball left/right → rotation

⚫ Ball lost → stop

✅ Result: Stable, low-latency performance observed.


###**8. Launch Procedure**
```bash
ros2 launch my_robot_bringup bringup.launch.py

This launches Gazebo, ROS–GZ bridges, TF publishers, RViz, and Ball Chaser node simultaneously.


###**9. Conclusion and Evaluation**

Robot demonstrated correct behavior and full ROS2–Gazebo integration.
Future improvements include Nav2 navigation, LiDAR, and Edge AI capabilities.


10. Links

GitHub: https://github.com/gokturkcan/CSE412_Assignment2_GoktürkCan

YouTube (Unlisted): https://youtu.be/lx7NfIekOpU
