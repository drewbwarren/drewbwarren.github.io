---
layout: project
title: Baxter Butler
date: December 8, 2017
category: projects
img: baxter_butler.png
description: This project combined all the principles that I gained from a class all about ROS, the Robot Operating System. I worked together on a team with four other students to program a Baxter robot to locate a cup on a table, grasp the cup, locate the right hand of a person in view of a depth sensing camera, and the bring the cup to the person's hand without tipping it over.
---
### Summary
{{ page.description }}

### Tasks

#### Locate the Cup

The first main task of the project was to find the cup and the grab it. Baxter starts with the arm in a position such that the end effector is horizontal and faces the table so that the hand camera can see the top of the table. All of that is done in a ROS node called `scan`. At the same time the `track_cup` node performs some computer vision filtering to locate the center of a red cup. Once the center of the cup is centered in the middle of the camera's view, the `move_to_cup` node is started, which executes a motion from the arm's current position to move directly to a grasping position.

#### Skeleton Tracker

At this point, the Asus Xtion camera (a simplified version of the Xbox Kinect) is used to locate the position of a person's right hand. This is done using the `skeletontracker_nu` package developed by Northwestern's NxR lab. This package filter's the camera's data to identify separate people in its view and returns a basic skeleton of each person. The skeleton is just the set of 3D points that correspond to several basic joints, such as neck, shoulder, elbow, wrist, etc. Our `filter_V2` node filters through the set of skeletons to select only the person that is closest to Baxter and most directly in front of him. In the end, this node returns the 3D point corresponding to that person's right hand.

#### Constrained Motion

The final task is to plan a path from the arm's position where it grabbed the cup to the position of the person's hand with an orientation constraint such that the cup does not tip over. We used The MoveIt! package from ROS to do this path planning. At first we took the approach of giving MoveIt! the goal pose (the position of the person's hand) and planning the path in Cartesian space with an orientation constraint included. While this did work, the calculations took a long time. The final approach was to find a joint space solution for the goal pose and then feed those joint positions into MoveIt! to plan a path in joint space. For this aproach we actually removed the orientation constraint. Since the start pose and end pose have the same orientation, MoveIt! almost never created paths that change the orientation. While this is not the most robust solution, it did cut down the computation time greatly so that the overall performance was more refined.


