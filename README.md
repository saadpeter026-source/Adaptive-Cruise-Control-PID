# Adaptive Cruise Control (ACC) — PID Implementation
## Overview
In this project, we will analyze the implementation of Adaptive Cruise Control (ACC) compared to Traditional Cruise Control. An ACC system can overall increase the quality of the user experience in a vehicle due to integrations such as speed and distance controllers. Traditional Cruise control can maintain a set speed and cannot react to other vehicles on the road. If the vehicle (lead) ahead slows down, the driver (ego) must either deactivate the system by cancel state in the system, or use Emergency braking to fully stop Cruise Control. The project shows a build PID-based ACC system that detects the distance and speed of a lead vehicle. The system has implemented logic that automatically switches between Speed Control (tracking a target velocity) and Spacing Control (maintaining a safe gap). A stateflow model logic will manage driver inputs, and a Nonlinear Plant that simulates real-world physics, such as vehicle mass and aerodynamic drag. The controller uses a PID loop to calculate the required acceleration or braking force. For a better understanding of the system, I verified the performance of the PID-based controller against the MATLAB Model Predictive Control (MPC) documentation. I used the same initial conditions and vehicle parameters to see how well a reactive PID controller mimics a predictive MPC system.

## High-Level Control Diagram.
<img width="963" height="431" alt="image" src="https://github.com/user-attachments/assets/838e9d98-fc8f-45b4-a922-59ee1013a75f" />

## References

* [1] MATLAB Documentation. "Adaptive Cruise Control System Using PID Controller." [Link](https://www.mathworks.com/help/control/ug/adaptive-cruise-control-system-using-pid-controller.html)
* [2] MathWorks. "Trigonometric Function Block Reference." [Link](https://www.mathworks.com/help/simulink/slref/trigonometricfunction.html)
* [3] MathWorks. "PID Controller Block Reference." [Link](https://www.mathworks.com/help/simulink/slref/pidcontroller.html)
