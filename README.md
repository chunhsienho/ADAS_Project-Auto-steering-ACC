# ADAS_Project-Auto-steering-ACC-
This is the final project of EECS 461 in University of Michigan. The goal of the project is to simulate Auto steering and Adaptive Cruise Control.


[//]: # (Image References)

[image1]: ./picture/autosteering.jpg "Autosteering"
[image2]: ./picture/ACC.jpg "ACC"



ACC and self-steering are more and more used in automotive industry. 
Like recently, Honda implements Honda Sensing in 2016 in its new civic and accord. 
In this project, we use embedded system to achieve the same functions for a virtual vehicle. 
We use Simulink to establish vehicle models, and generating C code for the embedded system. 
The car can be driven by human, or work in ACC mode to keep a speed or distance from the vehicle ahead. 
Also, the car can be self-steering to keep in the middle of the road.

There are six file you would have in this project

 DrivingSimVR: Folder that contains the Windows graphics program
 parameters.m: MATLAB script to set model parameters
 Final project TEMPLATE.slx: Template Simulink model for the Project
 controllers.slx: Contains a position and a speed controller
 rappid 564xl user copy required les.m: place in the same folder as the main project Simulink file.
 Demo.mp4: show the result of ACC and auto-steering


Automatic Steering Controllers

![alt text][image1]


Inputs of automatic steering controller are enable command, desired lateral displacement (a constant value, n_des), actual lateral displacement (n), steering angle (delta). The output of this block is auto steering torque. A discrete time PD controller is implemented to get a reference angle. Then the error between this reference angle and delta would go through a discrete time PID controller which yields an output value of the auto torque.
When tuning the value of controllers, we followed the method that if the car make multiple attempts to make a turn, the result is underdamped, the value of Kp should be increased; if the oscillation is unstable, the value of Kp should be decreased. If there is a big oscillation and it takes a long time to get the car stable, the value of Kd should be increased to make the oscillation small. The value of Ki was very small.

Adaptive Cruise Control

![alt text][image2]


