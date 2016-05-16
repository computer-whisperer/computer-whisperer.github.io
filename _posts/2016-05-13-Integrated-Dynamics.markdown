---
layout: post
title:  "Integrated Dynamics"
tags: FRC 2016 Smeagol Python Theano
---

Driven by my experience in the FRC game Recycle Rush, I spent the summer and fall of 2015 learning more about higher-level methods for robotic 
motion control. I dual enrolled in a nearby community college to learn Calculus I, Calculus II, and Physics I -- helping me to understand the 
collegiate-level whitepapers that describe the algorithms I needed. This was when I first discovered the field of Optimal Control -- using a full simulation of 
your robot combined to find the robot controller necessary to optimize a given cost function. The possibilities of such a system astounded me, 
and I started work on Integrated Dynamics.

It all began when I stumbled on the whitepaper [Learning of Closed-Loop Motion Control](http://www.adrl.ethz.ch/archive/p_14_iros_ballbot_cameraready.pdf). 
While an unlikely entry point, It was the first mention I had seen of what was Model-Based motion control. It highlights two algorithms which can be used to
generate discreet-time state-space controllers for any robot automatically. Of these algorithms, one in particular seemed applicable to the challenges I 
regularly experience in FRC -- iLQG. I found a great example implementation of this algorithm written by Yuval Tassa in Matlab, and spent the next three 
months porting it to Python.

That got me started. After playing around with iLQG for a while, I realized that the most important component of any model-based algorithms, such as this, 
is to have an accurate model. To this end, I started my long journey towards designing a robotics simulator that is realistic enough to correctly optimize a 
controller for any situation. Another algorithm that relies on an accurate physics engine is a linear-quadratic estimator -- the extended kallman filter. This 
uses a real-time simulation of your robot, combined with any available sensors, to provide a running estimation of your robot's complete state. This is a crucial 
piece to the execution of any state-space controller, such as the one produced by iLQG.

Before I started work on the simulator, I discovered an amazing python library written by the Neural Network community. Theano is, put simply, a linear algebra compiler. 
You can use it to build complicated mathematical expressions in native python which can be optimized and compiled to machine code. As you build your mathematical function, 
you can easily algebraically differentiate any part of it -- making it perfect for simplifying the elements of my physics engine.

One of the difficulties I recognized early on is how to realistically simulate DC motors in real-world units. As simple of a mechanism as a motor tied to a 
metal block represents an equation I had never heard of before -- an ODE (Ordinary Differential Equation). This is because the torque applied from any motor is 
a linear function of its rotational velocity, which increases as torque is applied. The most straightforward solution, euler integration, proved to be too coarse 
for many physical systems I attempted to simulate. After many questions asked online, I came upon two methods -- an exact solution for a scalar problem and a taylor 
series approximation for a vector problem. Neither were ideal, but the taylor series proved the best method given my constraints.

By the time of the 2016 FRC Kickoff, I had this simulator in a largely functioning state -- and I had hoped with little effort to finish it for use in the final robot I 
would build as a member of that team. I encountered many issues, however, that sprung from my overall inexperience. The largest difficulty seemed to spring from my 
friction model, which relied largely on my ode solver to function. Despite my intention, this model proved to be discontinuous in areas, and caused mysterious NANs to 
crop up when I tried to compute the overall simulation derivatives. This hampered my overall progress, and due to other time-consuming involvement on my robotics team, 
I was unable to resolve these issues in time to put it to work on the real robot.

After the end of my team's robotics season, I redoubled my effort to finish this library. Part of this was for me to take a step back and re-design elements that had caused 
me trouble. One of the improvements I am in the process of making is to perform all physics calculations in three dimensions, rather than the simplistic two-dimensional 
analogs I had used previously. The revamped physics engine is inspired primarily by [MuJoCo](http://www.mujoco.org/), a simulator designed for model-based robotics controllers 
such as I am using. As I am building this, I am learning more and more about how to represent articulated objects in full three-dimensional space. This is turning out to be orders 
of magnitude more difficult than the two-dimensional rigid-body simulations I had used previously. Still, difficulty has not deterred me in the past, and I hope to get this 
working in the weeks to come.

Software source links:

 - [Integrated Dynamics on Github](https://github.com/computer-whisperer/integrated-dynamics)

