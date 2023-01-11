---
layout: project
title: Balancing Platform Robot
date: March 23, 2018
category: projects
img: platform_rolling.png
description: This individual project for the Northwestern MSR program was an exploration of feedback control systems on a real world dynamic system. The device used is a 6-degree-of-freedom Stewart platform actuated by six servo motors. Feedback for the position of the ball is provided by a USB camera with some image processing applied to the video. 
video: "https://www.youtube.com/embed/3yrvO972--8?rel=0&amp;showinfo=0"
---

### Goals

The purpose of this project was to explore various methods of control on a real-world system. Specifically, the goal was to make a robot that could juggle a ping pong ball in a controlled manner. So far the platform is developed enough to control the ball's position by rolling it around. This will translate well into control of juggling because the same roll and pitch control needs to be applied. The next steps are to gain an understanding of a dynamic model for a bouncing ball and to develop the necessary trajectory in the platforms motion to transfer energy to the ball vertically.

### Components

#### Hardware
The device is a 6-degree-of-freedom Stewart platform. Credit for the design of the platform goes to [Full Motion Dynamics][fmd], and I found all the files and plans on [this page][instr]. The six servo motors on the bottom are controlled by an Arduino Uno. All the kinematics for the platform are performed on the Arduino. Desired roll and pitch angles as well as desired vertical position are sent to the Arduino over serial link and from those values it computes the inverse kinematics to find the necessary servo motor signal to achieve the desired motion. It is also possible to control the platform's position in the horizontal plane and its yaw, but so far these controls have not been needed.


#### Feedback

The sensor providing feedback on the ball's position in this system is a Logitech USB camera. The camera sits on a tripod above the platform and looks down on it at an angle. The video is fed into a pipeline to extract the ball's position using OpenCV functions. The code first applies a filter to locate the green tape along the platform and extracts corner edges from that shape. Then the image conatined within those four corners is project into a new square image. This new image provides an orthogonal view of the platform with the ball on it. The orthoganl image is then filtered to find the orange ping pong ball and it reports the position of the ball within the image and relates that to position on the platform. This may not be the most robust sensor and method of obtaining the ball's position, but I wanted to explore a more interesting sensor and the capabilities of computer vision in a dynamic system. Weaknesses of this sensing include the low framerate of the USB camera (30 Hz) and the fact that any time the view of the platform is obstructed by something else the image processing falls apart.

#### Control

Several types of controllers were attempted on this system. A PID controller was developed first for its simplicity. The velocity of the ball is approximated using the ad-hoc "dirty derivative" differentiation structure. Due to imperfections in the construction of the platform, its measurements, and noise in the ball position readings, the PID controller was barely stable. A state space controller for the ball was developed next with the states being the ball's x and y position and velocity on the platform. This controller provided marginally better control. Real success in stabile control of rolling the ball came from implementation of an LQR controller. Setting the LQR to penalize error in the ball's position stronger than error in its velocity and penalizing control effort a relatively high amount led to the most stable control so far. That is what can be seen in the video.

Excluding the kinematics for the platform, all the control was developed in Python within a ROS package. The [github repo][git] for this project contains the entire ROS package for the platform, and further information on how the package is structured can be found on the readme for the repo.

[instr]:http://www.x-sim.de/forum/viewtopic.php?f=38&t=913
[fmd]:https://www.youtube.com/watch?v=j4OmVLc_oDw&t=4s
[git]:https://github.com/drewbwarren/bouncing_platform_package
