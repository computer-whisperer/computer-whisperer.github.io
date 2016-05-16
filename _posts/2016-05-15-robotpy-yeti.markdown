---
layout: post
title:  "My work with RobotPy and Yeti."
tags: Python FRC
---

Officially, FIRST supports three programming languages for FRC robots (LabVIEW, C++, and Java). As my team's main software developer, I used LabVIEW for the first two robots 
we built. In the fall of 2014, however, I decided to try Python as an alternative. While not an officially supported language, it is possible to use Python in FRC robots 
thanks to RobotPy, an open source port of the FRC control libraries into python. My switch to Python also coincided with the release of a new robot controller -- the RoboRIO. 
This platform change necessitated a rewrite of the RobotPy libraries, and I took this opportunity to become a contributor to the project. This gave me much experience with how 
to collaborate online with other developers, and how to receive critique of my work.

Another piece of software I started designing at this time was a software development framework for use on top of RobotPy. Yeti effectively isolates the robot-specific 
python code of your robot into “Modules” – independent python files dynamically loaded at run-time. Modules can be freely loaded, unloaded, replaced, and modified at any 
time. This allows you to easily build structured robot programs, with mechanisms to promote rapid-development and in-game failure recovery. Yeti also comes with a clean, 
built-in WebUI for loading, unloading, and reloading live modules. This allows you to make on-the-fly programming changes -- loading your new code without even leaving 
teleoperated mode.

![Yeti's WebUI](/assets/yeti-webui.png)

Yeti has proven a very useful tool for the two years we used it, and has saved us many times from last-minute typos I make when I am in a hurry. I can rely on it to 
"just work" while I focus on other parts of the robot software.

Software source links:

 - [Yeti on Github](https://github.com/computer-whisperer/Yeti)