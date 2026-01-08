# Subsystem 2: ACC and PID Controller:
<img width="1138" height="654" alt="image" src="https://github.com/user-attachments/assets/7d2d4ee9-891a-46b4-9694-9c6effe59adf" />

## Overview
A PID (Proportional-Integral-Derivative) controller is an important, fundamental piece of any control system design. It consists of three components: Proportional (P), Integral (I), and Derivative (D). Proportional gain generates an output directly proportional to the current velocity error, which is the difference between the target and the actual velocity provided by the Adaptive Cruise Control (ACC) subsystem. If the ego vehicle (the vehicle being controlled) is far from the target speed, the P gain applies a larger force to quickly close the gap. The Integral gain accumulates the error over time, ensuring that the vehicle eventually matches the exact target speed by reducing the steady-state error that the Proportional gain may miss. The Derivative gain responds to the rate of change of the error, helping to prevent the vehicle from overshooting or oscillating around the target speed. In this context, e(t) represents the difference between the Target Velocity from the ACC logic and the Ego Velocity, which is the car's actual speed.

In this system-level design, we will not be utilizing the other fundamental controller, Model Predictive Control (MPC); however, we will compare how a PID system works over MPC by analyzing a specific MATLAB documentation of an Adaptive Cruise Control System implemented by MathWorks. While MPC uses an internal model to predict future states and solve optimization problems, our design uses a PID Controller to provide a direct response based on current, past, and predicted error. This PID controller translates velocity error into engine force by summing three distinct terms.

## Individual PID Components
* **Proportional (P):**
  $$P = K_p \cdot e(t)$$

* **Integral (I):**
  $$I = K_i \int_{0}^{t} e(\tau) d\tau$$

* **Derivative (D):**
  $$D = K_d \frac{de(t)}{dt}$$

## Full PID Control Law Equation
$$u(t) = K_p e(t) + K_i \int_{0}^{t} e(\tau) d\tau + K_d \frac{de(t)}{dt}$$










<img width="1321" height="673" alt="image" src="https://github.com/user-attachments/assets/cccc1d7c-84e3-4a40-93c9-e212195028a4" /> 

