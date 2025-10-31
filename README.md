# CSE412 Robotics Course – Assignment 2
### Build Your Own Robot (Diff Drive + Camera + Ball Chaser)

**Student:** Göktürk Can  
**Student No:** 230611501  
**Instructor:** Asst. Prof. Dr. Abdurrahman Bayrak  
**Semester:** Fall 2025  
**Language Used:** Python  
**ROS2 Distro:** Humble  
**Gazebo:** Harmonic  

---

## 🔧 Project Description
This project implements a differential-drive robot in Gazebo Harmonic with a mounted camera and a `ball_chaser` node that follows a white ball visible in the camera image.

The system integrates:
- URDF + TF structure verification in RViz  
- Diff drive control through `/cmd_vel`  
- Camera stream through `/camera/image_raw`  
- Ball tracking logic implemented in Python  

---

## 🧩 Packages
| Package | Description |
|----------|--------------|
| `my_robot_description` | URDF, meshes, RViz, and world files |
| `my_robot_bringup` | Launch files for Gazebo, RViz, publishers, and nodes |
| `my_robot_chaser` | Ball-following node implementation |
| `my_robot_gazebo` | Simulation world and model setup |

---

## 🧠 Launch Procedure
```bash
ros2 launch my_robot_bringup bringup.launch.py

🎬 **YouTube (Unlisted)**  
👉 https://youtu.be/lx7NfIekOpU

