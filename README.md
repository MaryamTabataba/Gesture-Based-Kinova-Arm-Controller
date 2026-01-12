# Gesture-Based-Kinova-Arm-Controller
Built a computer-vision control system using OpenCV to mirror a user’s arm movements and dynamically control a Kinova robotic arm in real time with ROS2 and Python.

This project is from a Lab for Introduction to Robotics course.
It requires: 
Ros2
Ubuntu 20

To run, you must also clone the following github repos:

Clone https://github.com/YorkCFR/kinova/tree/main/kinova_ws/src/kinova_gen3/kinova_gen3 . 

Add the file kinova_gen3_command.py to kinova/kinova_ws/src/kinova_gen3/kinova_gen3. 

The code for Yolo Pose from https://github.com/YorkCFR/CPMR3/tree/main but edited for this project. 

To run, clone CPMR3 github, replace yolo_pose.py in CPMR3/ros2_ws/src/cpmr_ch12/cpmr_ch12 with the one in this github repo. 

# What it does
If only the left hand is above the shoulders by the distance in image coordinates from the eyes to the shoulder, move the arm so that it is at (0.10, 0.20, 0.10).

If only the left hand is below the shoulders by the distance in image coordinates from the eyes to the shoulder,, move the arm so that it is at (-0.10, 0.20, 0.10).

If only the right hand is above the shoulders by the distance in image coordinates from the eyes to the shoulder,, move the arm so that it is at (0, 0.10, 0.10).

If only the right hand is below the shoulders by the distance in image coordinates from the eyes to the shoulder,, move the arm so that it is at (0, 0.30, 0.10).

If both hands are above the shoulders by the distance in image coordinates from the eyes to the shoulder,, move the arm to (0, 0.20, 0.10).

If none of the properties above are true, don't move the arm.

# To Run
Clone this Github repo, along with https://github.com/YorkCFR/CPMR3/tree/main.

Replace yolo_pose.py in CPMR3/ros2_ws/src/cpmr_ch12/cpmr_ch12 with the one in this github repo. 

Clone this Github repo, https://github.com/YorkCFR/kinova/tree/main/kinova_ws/src/kinova_gen3/kinova_gen3 . 

Add the file kinova_gen3_command.py to kinova/kinova_ws/src/kinova_gen3/kinova_gen3. 

Make sure that you have a video camera attached to your machine and that it is available on /dev/video0 and that you can access it.

Then Install ultralyics

pip3 install -U ultralytics

Then

ros2 run cpmr_ch12 opencv_camera 
will run the node that captures the camera.
ros2 run cpm_ch12 yolo_pose
This will (if necessary) download the yolov8 weights and start up the node. Note that by default the node will run on the cpu. If your hardware has cuda support, you can change this so it will use it.

Make sure that you have the ros2 code to talk to the robot arm. 


