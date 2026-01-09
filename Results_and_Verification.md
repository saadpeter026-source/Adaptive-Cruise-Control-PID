# Comparing PID and MPC for Cruise Control

## Overview
In this final seciton, we will discuss 3 types of scenarios in a ACC system, and test it to ensure that the system if working. 

1.Performance Benchmarking
* We test the system using the same conditions as the Matlab documentation **$V_{set}=30$ m/s**.
* This confirms our PID tuning is correct and can follow a lead vehicle accurately.
* It shows the car handles non-linear drag while keeping a safe distance.

2. High-Speed Highway Test
We increase the speed to highway levels (e.g., 40 m/s) to test the car under more stress.This helps us see how aerodynamic drag affects the controller at higher velocities.We observe if the PID can still maintain the safety gap when air resistance is high.Road Grade Disturbance (The Hill)We place the ego vehicle on a hill while the lead car stays on flat ground.This tests how well the controller handles gravity pulling the car backward.We prove the Integral (I) term works to add extra throttle to stay at the correct distance.
