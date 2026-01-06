# Adaptive-Cruise-Control-PID
## Overview
In this project, I analyzed the implementation of Adaptive Cruise Control (ACC) compared to Traditional Cruise Control.

The Problem: > Traditional Cruise control cannot react to other vehicles. If a lead vehicle slows down, the driver must manually deactivate or cancel the system.

The Solution: > This PID-based ACC system automatically switches between:

Speed Control: Tracking a target velocity.

Spacing Control: Maintaining a safe gap using radar feedback.

The Design: > * Stateflow Logic: Manages driver inputs and system states.

Nonlinear Plant: Simulates real-world physics like mass and drag.

PID Controller: Calculates the required acceleration or braking.

Benchmarking: > I verified the performance against the MATLAB Model Predictive Control (MPC) documentation using identical parameters to compare a reactive system to a predictive one.


