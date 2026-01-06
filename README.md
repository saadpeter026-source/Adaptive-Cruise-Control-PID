# Adaptive Cruise Control (ACC) — PID Implementation
## Overview
In this project, we will analyze the implementation of Adaptive Cruise Control (ACC) compared to Traditional Cruise Control. An ACC system can overall increase the quality of the user experience in a vehicle due to integrations such as speed and distance controllers. Traditional Cruise control can maintain a set speed and cannot react to other vehicles on the road. If the vehicle (lead) ahead slows down, the driver (ego) must either deactivate the system by cancel state in the system, or use Emergency braking to fully stop Cruise Control. The project shows a build PID-based ACC system that detects the distance and speed of a lead vehicle. The system has implemented logic that automatically switches between Speed Control (tracking a target velocity) and Spacing Control (maintaining a safe gap). A stateflow model logic will manage driver inputs, and a Nonlinear Plant that simulates real-world physics, such as vehicle mass and aerodynamic drag. The controller uses a PID loop to calculate the required acceleration or braking force. For a better understanding of the system, I verified the performance of the PID-based controller against the MATLAB Model Predictive Control (MPC) documentation. I used the same initial conditions and vehicle parameters to see how well a reactive PID controller mimics a predictive MPC system.

## High-Level Control Diagram.
<img width="963" height="431" alt="image" src="https://github.com/user-attachments/assets/838e9d98-fc8f-45b4-a922-59ee1013a75f" />

## Subsystem 1: Stateflow Logic
<img width="1330" height="931" alt="image" src="https://github.com/user-attachments/assets/dc8d0fc9-d6bf-42b1-b83b-960cb10ac29e" />

SET: This state initializes the system by setting the target_speed and stored_speed to 30 units while capturing the current vehicle velocity in memory.
Accelerate (Accel): While the button (btn == 2) is held, the system performs a "During" action to increase the target_speed by 0.05 units per time step.
Decelerate (Deccel): While the button (btn == 3) is held, the system performs a "During" action to reduce the target_speed by 0.05 units per time step.
Resume: This state resets the target_speed to the stored_speed previously saved in memory when the resume button (btn == 4) is pressed.
OFF / Cancel: The system enters this state to set the target_speed and active_flag to 0, effectively disabling the cruise control.
Safety: The transition to the OFF state has a [brake == 1] condition, ensuring the brake signal always has priority to shut down the system.
