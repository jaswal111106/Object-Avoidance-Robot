Object Avoidance Robot
________________________

An Arduino-based autonomous robotic vehicle that detects obstacles in its path using an ultrasonic sensor and automatically changes direction to avoid collisions, without any manual control.

Overview
___________

The Object Avoidance Robot is a self-navigating platform built around an Arduino Uno and an HC-SR04 ultrasonic sensor. The robot continuously measures the distance to objects ahead of it, and when an obstacle is detected within a predefined range, the Arduino processes this data and executes a turning maneuver to steer clear of it before resuming forward motion.
This project demonstrates the practical integration of sensor interfacing, real-time distance measurement, decision-making logic, and motor control within a single embedded system, and serves as a foundational platform for understanding autonomous robotic navigation.

Objectives
_____________

Design an autonomous robot capable of detecting and avoiding obstacles without human intervention. Implement real-time distance measurement using an ultrasonic sensor. Develop an obstacle detection and navigation algorithm based on that measurement. Understand motor control and embedded system programming in the context of autonomous decision-making. Build a low-cost robotic platform suitable for learning autonomous robotics.
Hardware Components
The system is built around an Arduino Uno, which handles sensor data processing and navigation logic. An HC-SR04 ultrasonic sensor is mounted at the front of the chassis to continuously measure distance to obstacles. A single L298N motor driver module powers and controls four DC geared motors, arranged as two pairs on either side of the chassis and wired in parallel per side so each pair receives the same control signal. A battery pack supplies power to the system, with a power switch for control, and jumper wires complete the connections.

Software
___________

The firmware is developed in the Arduino IDE using Arduino C/C++. The core logic involves triggering the ultrasonic sensor, timing the echo response, converting that timing into a distance value, and using that value to drive a decision loop that controls the motor driver.

Working Principle
__________________

The HC-SR04 ultrasonic sensor operates by emitting a short ultrasonic pulse and measuring the time taken for the reflected pulse to return after striking an object. Since the speed of sound in air is known, the Arduino converts this echo time into a distance value using the standard time-of-flight relationship, where distance is proportional to the elapsed time multiplied by the speed of sound and divided by two, to account for the pulse traveling to the obstacle and back.
This distance value is continuously compared against a predefined threshold that defines the minimum safe clearance in front of the robot. If the measured distance is greater than this threshold, no obstacle is considered present, and the robot continues moving forward by driving all four motors in the same direction.
If the measured distance falls below the threshold, the Arduino interprets this as an obstacle in the robot's path. It immediately halts forward motion by stopping all four motors, then executes a turning maneuver by driving the left and right motor pairs in opposite directions or at different speeds, rotating the robot until the ultrasonic sensor no longer detects an obstacle within the threshold range. Once a clear path is confirmed, the robot resumes forward movement automatically.
Since the four motors are wired as two pairs, one for each side of the chassis, all differential steering during turns is achieved by controlling these two pairs independently through the L298N's two output channels, rather than controlling each motor separately. This entire sensing, decision, and actuation cycle repeats continuously in a polling loop, allowing the robot to navigate autonomously through an environment with obstacles.

Applications
______________

This project is suited for autonomous mobile robotics, educational demonstrations, smart navigation prototypes, early-stage warehouse automation concepts, service robot prototyping, robotics competitions, and general embedded systems learning.

Future Improvements
____________________

Planned or possible extensions include mounting the ultrasonic sensor on a servo motor for wider-angle scanning, integrating IR sensors for enhanced obstacle and edge detection, combining line-following and obstacle avoidance into a hybrid navigation mode, adding Bluetooth or Wi-Fi manual override capability, incorporating camera-based computer vision for more advanced object recognition, exploring AI-based path planning, enabling IoT-based remote monitoring, and eventually implementing SLAM for autonomous mapping and localization.

Author
__________

Deeksha Jaswal
B.Tech, Electronics and Communication Engineering
Focused on embedded systems, robotics, IoT, and AI-driven hardware.
