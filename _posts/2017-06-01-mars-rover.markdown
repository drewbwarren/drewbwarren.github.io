---
layout: project 
title: University Rover Competion 
date: June 1, 2017
category: projects
img: rover_and_arm.jpg
description: For my senior capstone project at Brigham Young University, I was a part of the Mars Rover team. The project involved designing, constructing, programming, and operating a rover to participate in the University Rover Challenge hosted by the Mars Society. I was mainly responsible for design, control and operation of the robot arm, as well as work on the drive system. The BYU rover was a success and our team earned fourth place in the competition against teams from 35 universities from around the world.
video: "https://www.youtube.com/embed/APVvw9Aw8Wo?rel=0&amp;showinfo=0" 
---

#### University Rover Competition

[The Mars Society][mars] is a volunteer organization made up of professionals and space connoisseurs whose primary goal is to further the public knowledge of and promote the exploration of Mars. One of the outreach projects that they do to push for Mars exploration is an academic competition called the [University Rover Challenge][urc]. In this competition, universities from all over the world enter their designs for a world-class Mars rover for review. In 2017, a total of 82 teams submitted their designs, and 32 were chosen to participate in the competition. Those 32 teams brought their rovers to the Mars Society's Desert Research Station in June 2017 to operate the rover through four different tasks made to reflect actual responsibilities that a rover could have. As part of the Brigham Young University Mars Rover team, I helped the team to take [fourth place][four] at the competition.

#### Design Process

In addition to competing in the University Rover Challenge, this project served as a senior capstone project for my B.S. in Mechanical Engineering at BYU. The capstone projects at BYU offer students an opportunity to apply the design process to real engineering problems that need to be solved. Together with my team, we proposed requirements shape how the design evolved, we established desirability goals that would make our product a world-class rover, and we defined performance measures that would help us and our sponsor know if the rover and the design were meeting requirements. Doing a practical project using the design process helped me learn how to set goals, requirements, and tests, to push designs through an approval process, and to do it all on a team of 16 engineers.

#### Design 
My main responsibilities for the project were in the design, control, and operation of the robot arm on the rover, as well as the microcontrollers for the drive system. There was a subteam in charge of the chassis, and they were the ones who designed the wheels and sized the motors for each wheel. For the motors they chose a brushless DC motor and gearbox combination built by Anaheim Motors. To complete the wheels they needed my help on the electrical and control aspects. I found and ordered brushless DC motor drivers, connected all the circuits between the motors, the motor drivers, and the main microcontroller, and I programmed the functionality of the drive system.

Mostly I worked on the robot arm on the rover with two other students. Two of the four tasks of the competition required the rover to manipulate and transport objects in the field, and we chose to design and build a serial link robot arm to perform those tasks. The rover from the previous team still had an arm on it, though it had several flaws. The motors in the wrist had not been strong enough to lift the max load necessary in competition and most of the joints had a wide range of play just because gears were loose-fitting.

In redesigning the arm, my subteam and I had to decide which features to keep, which ones to change, and which ones to throw out. We did our own analysis, of the arm geometry, looking at link lengths and the orientation of each joint, to obtain a good reachable workspace from the arm. We kept the same configuration of joints but modified the link lengths to give the arm more space to work in.

The best part of the old arm was the end effector or gripper. We kept the original gripper, but we changed the way it attached to the motors that move it. The wrist had been actuated by one Dynamixel motor to tilt the gripper up and down and another Dynamixel to spin it. We used a bevel gear between these two motors and the gripper so that the two of them worked together to lift and twist the wrist. This increased the maximum load, the wrist could lift without any significant cost.

In an effort to reduce weight, we redesigned the two main links of the arm to be carbon fiber pipes. We moved away from a design with gearbox-motor modules to using linear actuators for the joints that would do the heavy lifting. In our analysis we saw that two of the joints would provide most of the force when lifting objects, so for those two joints we chose linear actuators to move the joints. The linear actuators provided more than enough force to lift the maximum load and their weight was less than the weight of a motor that could provide the necessary torque.

I worked in large part with the electrical subteam to integrate control of the arm motors into the complete system. We used motor drivers built by Pololu to control each joint. The main microcontroller was a PSoC 5 from Cypress Semiconductor. All commands for each motor came from the onboard computer, an Nvidia Jetson TX1, to the PSoC through a serial connection. The PSoC then sent appropriate serial commands to the Pololu motor drivers to actuate the joint motors. The PSoC was also responsible for sending the correct PWM signals to the drive wheel motor controllers to actuate the wheels.

Our original goal in designing the arm was to have a 6 joint arm that incorporated inverse kinematics so that the user could input a Cartesian point and the arm would move each joint the right way to put the gripper at that point. Due to time constraints, we ended up with a 5 joint arm that was controlled by moving each joint individually. Controlling a robot arm joint-by-joint like this is difficult, but the time we had left was better spent practicing with the arm as it was than trying to implement inverse kinematics. Having a good understanding of the capabilities and limitations of the arm was essential for a good performance at the competition. The video featured here shows the rover working through the Equipment Servicing Task where we were asked to perform several manipulation actions that a real rover would be required to do. I was operating the arm and my teammate was driving the rover, and the only vision we had was what we could see from the cameras we had on the rover.

[mars]:http://www.marssociety.org/
[urc]:http://urc.marssociety.org/home
[four]:http://urc.marssociety.org/home/about-urc/urc2017-scores


