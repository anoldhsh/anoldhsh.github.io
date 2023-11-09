---
layout: post
title:  Vision-Based Automatic Table Tennis Machine
# date:   2018-07-24 15:01:35 +0300
image:  TableTennis.gif
tags:   Undergraduate_project
description: 
---

* The "Vision-Based Automatic Table Tennis Machine" project, developed for the 4th GIST Creative Convergence Competition in 2020, where it received the GIST Presidential Award. 

* This project was conceived with the objective of creating an autonomous table tennis machine capable of playing table tennis with human opponents. 

* The core of this system lies in its ability to interact dynamically with a fast-moving object - the table tennis ball - and respond in a manner akin to a human player.

* At the heart of the system are two webcams, which are used to capture the real-time 3D coordinates of the table tennis ball. These coordinates are processed using LabView and Matlab to accurately track the ball's trajectory. The system then employs a simple parabolic equation to predict the future position of the ball. 

* This prediction is essential for the system's next phase - planning the movement of a 5-degree-of-freedom serial robot arm, which is coupled with a linear actuator. The robot arm is directed to the predicted position of the ball, where it executes a swing motion to hit the ball back to the opponent.

* A critical aspect of this system is the adjustment of the swing angle. The system is programmed to alter the swing angle based on the trajectory of the incoming ball, with the aim of returning the ball to the center of the court. This strategic adjustment mirrors the decision-making process of a human table tennis player, enhancing the machine's capability to provide a challenging and realistic playing experience. 

* The system's efficacy was demonstrated through its ability to sustain a rally with human players, successfully completing 30 ball exchanges in a rally.