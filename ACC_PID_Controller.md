# Subsystem 2: ACC and PID Controller:

## Fundamentals of PID
<img width="1138" height="654" alt="image" src="https://github.com/user-attachments/assets/7d2d4ee9-891a-46b4-9694-9c6effe59adf" />

## Overview
A PID (Proportional-Integral-Derivative) controller is an important, fundamental piece of any control system design. It consists of three components: Proportional (P), Integral (I), and Derivative (D). Proportional gain generates an output directly proportional to the current velocity error, which is the difference between the target and the actual velocity provided by the Adaptive Cruise Control (ACC) subsystem. If the ego vehicle (the vehicle being controlled) is far from the target speed, the P gain applies a larger force to quickly close the gap. The Integral gain accumulates the error over time, ensuring that the vehicle eventually matches the exact target speed by reducing the steady-state error that the Proportional gain may miss. The Derivative gain responds to the rate of change of the error, helping to prevent the vehicle from overshooting or oscillating around the target speed. In this context, e(t) represents the difference between the Target Velocity from the ACC logic and the Ego Velocity, which is the car's actual speed.

In this system-level design, we will not be utilizing the other fundamental controller, Model Predictive Control (MPC); however, we will compare how a PID system works over MPC by analyzing a specific MATLAB documentation of an Adaptive Cruise Control System implemented by MathWorks. While MPC uses an internal model to predict future states and solve optimization problems, our design uses a PID Controller to provide a direct response based on current, past, and predicted error. 

## Individual PID Components
* **Proportional (P):**
  $$P = K_p \cdot e(t)$$

* **Integral (I):**
  $$I = K_i \int_{0}^{t} e(\tau) d\tau$$

* **Derivative (D):**
  $$D = K_d \frac{de(t)}{dt}$$

## Full PID Control Law Equation
$$u(t) = K_p e(t) + K_i \int_{0}^{t} e(\tau) d\tau + K_d \frac{de(t)}{dt}$$

$$
\begin{array}{|l|c|c|}
\hline
\textbf{Controller Parameter} & \textbf{Symbol} & \textbf{Value} \\
\hline
\text{Proportional Gain} & K_p & 370 \\
\hline
\text{Integral Gain} & K_i & 3 \\
\hline
\text{Derivative Gain} & K_d & -340 \\
\hline
\text{Filter Coefficient} & N & 6 \\
\hline
\end{array}
$$

## ACC Subsystem
<img width="1321" height="673" alt="image" src="https://github.com/user-attachments/assets/cccc1d7c-84e3-4a40-93c9-e212195028a4" /> 

## Overview
There are two important aspects of adaptive features in a Cruise Control system: Speed controller, Distance controller. An ego vehicle on the road must also understand how to intervene and switch conditions in a scenario in order to prevent an accident from happening. First, the ego vehicle must understand that it should activate the condition of the speed controller if the lead vehicle is farther away. Second, the ego vehicle must understand that it should switch to the spacing or distance controller if it approaches the lead vehicle too close. Essentially, it must have logic to drive at a desired set speed as long as it maintains a safe distance. 

So, how can we implement this idea into mathematical equations? 

## Mathematical Representation of Speed Controller
$$V_{target} = V_{set}$$

where
* **$V_{set}$** - The desired cruising speed defined by the driver (e.g., $30 \text{ m/s}$).
* **$V_{target}$** - The reference speed sent to the PID controller.

## Mathematical Representation of Distance Controller
If we anyaalize the subsystem at the top, The first part of the math determines the safe distance based on the current speed of your car **$V_{ego}$** and a chosen time gap **$T_{gap}$**.

$$D_{des} = V_{ego} \cdot T_{gap} + D_{default}$$

where
* **$D_{des}$** - The safe desired distance to maintain.
* **$V_{ego}$** - The current velocity of the ego vehicle.
* **$T_{gap}$** - The time gap between vehicles, set to $1.4 \text{ s}$.
* **$D_{default}$** - The standstill distance, set to $10 \text{ m}$.

Addtionally, the velocity required to close or maintain that gap. It adjusts the speed of the lead car **$V_{lead}$** based on the distance error.

$$V_{follow} = V_{lead} + K_{d} \cdot (D_{rel} - D_{des})$$

where
* **$V_{target}$** - The final reference speed sent to the PID controller.
* **$V_{set}$** - The speed defined by the driver in cruising mode.
* **$V_{follow}$** - The speed required to maintain a safe gap.

## Relative Distance Equation
$$D_{rel} = x_{lead} - x_{ego}$$

where
* **$D_{rel}$** - The relative distance between vehicles.
* **$x_{lead}$** - The absolute position of the lead vehicle on the road.
* **$x_{ego}$** - The absolute position of the ego vehicle on the road.

## Switch Logic Equation
$$V_{target} = \min(V_{set}, V_{follow})$$

## Mode Summary Table:
| Condition | Operational Mode | Target Velocity Equation |
| :--- | :--- | :--- |
| $D_{rel} > D_{des}$ | **Speed Control** | $V_{target} = V_{set}$ |
| $D_{rel} \leq D_{des}$ | **Spacing Control** | $V_{target} = V_{follow}$ |
