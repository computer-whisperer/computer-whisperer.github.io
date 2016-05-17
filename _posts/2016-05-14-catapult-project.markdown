---
layout: post
title:  "Operation Catapult 2015 project: River ecosystem simulator."
tags: 2015 Python
---

In the summer of 2015, I attended Operation Catapult – a three-week STEM program at Rose-Hulman Institute of Technology. There I joined a team of three, and worked to 
develop a simplistic biological population simulator. This was written in python, and was designed to demonstrate the effects of invasive species on an ecosystem. 
Specifically, this simulator represented the impact of Asian Carp when introduced into an existing environment of plankton (prey), native fish, and pelicans (predators). 

![The finished river ecosystem simulator](/assets/catapult-project.jpg)

For me, the project ended up being a lesson in optimization. When I initially wrote the simulation engine, it was capable of modeling the Artificial Intelligence of up to 
100 entities. I was able to use various techniques to reduce the computational load, and performed some tasks (range calculations, entity position sorting, other O(n2) 
operations) in “lazy tics” at a much slower rate than the rest of the simulation logic. These improvements increased the capacity of the simulation to upwards of 700 
agents.

The finished project was successful, and properly demonstrated the detrimental effect of introducing agents with unbalanced traits into an environment.

Software source links:

 - [Ecosystem simulator on Github](https://github.com/computer-whisperer/catapult-2015-project)