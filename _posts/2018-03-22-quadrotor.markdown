---
layout: project
title: Autonomous Quadrotor from Scratch
date: March 22, 2018
category: projects
img: quadrotor.JPG
description: The controls for this quadrotor were developed from scratch. There are controllers attached to the roll, pitch, and yaw of the quadrotor as well as for its position in the room. An onboard IMU was used for the orientation control and an HTC Vive Lighthouse was used for sensing position relative to the inertial frame.
video: "https://www.youtube.com/embed/Rd4jxvpdiQA?rel=0&amp;start=4"
---

### Goals
In building this quadrotor I wanted some practical experience in applying controls algorithms on a physical system through embedded hardware. Quadrotors are very sensitive systems in the sense that very small factors such as perturbations in rotor speed or sensor noise can affect the stability of the flight. By the end of the project I developed 6 interconnected compensators actuating 4 rotors to control yaw, yaw rate, pitch, roll, height, and position in the horizontal plane.

#### Sensing
All the hardware for the quadrotor was provided by Northwestern University, most of it already assembled and configured. The quadrotor contained a 6-axis inertial measurement unit that reported inertial forces acting in three directions through an accelerometer and rotational velocities in three directions through a gyroscope. The data from the accelerometer was used to calculate roll and pitch angles. The gyroscope data was used for the rotational rates in the controllers. Additionally the quadrotor contained an IR sensor in collaboration with an HTC Vive Lighthouse placed above the quadrotor. The Lighthouse sends out an array of infrared beams and the sensor on the quadrotor receives them. In this way the sensor reports its position relative to the Lighthouse in three directions.

#### Controllers
I first developed controls for the pitch. I suspended the quadrotor using some string to effectively reduce the system to one degree of freedom. A PID controller was built around the pitch. It received data from the IMU about the pitch angle and rotational velocity and calculated the necessary rotor speeds needed to correct the pitch toward a target position. The same process was done for the roll. The target positions for these two controllers were then connected to an input from a joystick controller together with basic controls to raise or lower the speed of all four rotors to manually control the height. After tuning controllers, the joystick effectively sent commands to control the height, roll and pitch of the quadrotor making it function the same as any low-grade, off-the-shelf quadrotor.

At this point the HTC Vive sensors were introduced in the effort to develop autonomous position control. Another PD controller was built aroun the pitch controller for the x position of the quadrotor. It received as its input a target position, the feedback was the data from the Vive sensor, and the output was the target pitch for the previously built PID controller. Another PD controller like this was built around the roll to control y position. After tuning these controls the quadrotor could hold to a target position in the horizontal plane provided by joystick input. Work was done to accomplish the same for the height of the quadrotor, but time restraints limited the development of that controller.

