---
layout: project 
title: Mechatronics Course Ping Pong Ball Shooter 
date: December 9, 2015
img: ping_pong_shooter.jpg
category: projects 
description: During my undergradute studies, I participated in a mechatronics course project that involved creating a ping pong ball shooter robot for a competition. The robot was placed in the arena, had to collect ping pong balls from a dispenser, identify an active goal (one out of three), and shoot the balls into the goal. All of this was done autonomously. The hardware was built from laser-cut wood and acryllic, off the shelf motors and sensors, and fabricated printed circuit boards. The robot was controlled by a PIC32 microchip and programmed with C. I was personally tasked with converting all of the prototype circuits to more robust PCB's. The robot included an IR sensor with filtering to locate the active gate.
---

### Summary

During my undergraduate studies, I participated in a mechatronics course project with three other students that involved creating a ping pong ball shooter robot for a competition. The robot was placed in the arena, had to collect ping pong balls from a dispenser, identify an active goal, and shoot the balls into the goal - all completed autonomously.

### Design

Our team was completely responsible for designing a robot to complete the tasks of the competition and building it from scratch. As we learned about new concepts and electrical components in the course we would include each new feature to the design. We built the robot out of prototyping materials, prepared each subsystem on breadboards, and tested the robot extensively. 

The whole robot was controlled by a PIC32 microcontroller, the code was in C and was compiled on the PIC using a PICkit 3, and it was developed in MPLab X. The features and peripherals that we used to complete the task include interrupts, change notifications, clocking, control of brushed DC, stepper, and servo motors, and sensing with push buttons, IR sensors, and encoders.

#### Base

We laser cut a base from acryllic and attached two omnidirectional wheels and a caster to it. The wheels were actuated by stepper motors which were controlled from the PIC through Pololu motor drivers. The base was designed with a 90 degree angle in the front so that if the robot ran into a wall the omnidirectional wheels would allow it to slide into the corner to line up with the goals.

#### Sensing

Two push buttons on the front edges of the base sensed with the robot was driving into the wall or corner, and these buttons triggered change notification interrupts in the PIC. The goals and the ping pong ball dispenser in the arena were designated by emitting IR light at specified frequencies. I helped my team develop a sensor with and IR photodiode and a filter to distinguish between the goal and dispenser lights. 

#### Actuating

The dispenser was triggered by breaking a vertical laser beam. We placed a stick on the spindle of a servo motor and rotated the motor back and forth 6 times to fill the hopper with balls. The servo motor was controlled by sending the appropriate duty cycle of a square wave signal using the pulse width modulation feature of the PIC. The ping pong ball shooter was just a small DC motor that turned on to shoot the balls when the robot was in place.

#### Electronics

As we introduced new subsystems into the project our prototyping breadboards became increasingly complex, messy, and buggy. I took it upon myself to convert individual electrical subsystems to printed circuit boards once they were tested and ready for the change. I made all the designs in the PCB design freeware Eagle and printed all the boards on one-sided copper film boards from a mill.



