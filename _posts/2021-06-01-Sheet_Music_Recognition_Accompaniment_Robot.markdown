---
layout: post
title:  Creating an Accompaniment Robot that Can Automatically Recognize Sheet Music
# date:   2018-07-24 15:01:35 +0300
image:  PianoRobot.gif
tags:   Undergraduate_project
---

* The project "Creating an Accompaniment Robot that Can Automatically Recognize Sheet Music" endeavors to develop a robotic system capable of reading and performing music from sheet music autonomously. 

* The focal point of this project is the integration of optical recognition and robotic manipulation to facilitate an automated musical performance. This robot, equipped with a camera, employs Optical Character Recognition (OCR) technology and a specially trained model to interpret sheet music, identifying both the accompaniment chords and the tempo (beats per minute, bpm) indicated on the score.

* The initial phase of the project involved training the model with an OCR dataset to accurately extract the sound components of the chords from the sheet music. This process is crucial for the robot to discern the musical notation and translate it into a sequence of actions. 

* Subsequently, the project emphasizes the planning and execution of movements for two robotic manipulators, each with six degrees of freedom, including grippers. These manipulators are mounted on linear actuators, which enable them to navigate across a keyboard and accurately press the corresponding keys.

* A significant aspect of this system is the precise calculation of the movements and timing for the robotic arms. These calculations ensure that each arm presses the appropriate bass note (root note) and chord components at the correct timing, adhering to the rhythm and progression of the music as indicated by the bpm recognized from the sheet music. Once the path is set, the robot follows the predetermined trajectory, playing the recognized chords and maintaining the tempo throughout the performance.