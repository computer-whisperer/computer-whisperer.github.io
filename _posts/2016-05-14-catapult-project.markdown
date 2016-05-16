---
layout: post
title:  "Operation Catapult 2015 project: River ecosystem simulator."
tags: 2015 Python
---

In the summer of 2015, I attended Operation Catapult, a three-week STEM program, at Rose-Hulman Institute of Technology. The project my team of three selected was 
a simplistic biological population simulator, written in python, designed to demonstrate the effects of invasive species on an ecosystem. Specifically, this 
simulator represented the impact of Asian Carp when introduced into an existing environment of plankton (prey), native fish, and pelicans (predators). 

![The finished river ecosystem simulator](/assets/catapult-project.jpg)

For me, the project ended up being a lesson in optimization. When I initially wrote the simulation engine, it was capable of modelling the ai's of up to 100 entities. 
Using various techniques to reduce the computational load, and performing some tasks (range calculations, entity position sorting, other O(n<sup>2</sup>) operations) 
in "lazy tics" which occurred at a much slower rate than the regular simulation tics. These improvements increased the capacity of the simulation to upwards of 700 agents.

The finished project was pretty successful, and properly demonstrated the effect of introducing agents with unbalanced traits into the environment.

Software source links:

 - [Ecosystem simulator on Github](https://github.com/computer-whisperer/catapult-2015-project)