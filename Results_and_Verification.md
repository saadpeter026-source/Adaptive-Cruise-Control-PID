# Comparing PID and MPC for Cruise Control

## Results and Discussion Overview
In this final section, we will discuss three types of scenarios in an ACC system and test it to ensure that the system is functioning properly.

### 1. Performance Benchmarking
* Testing with documentation conditions where $V_{set} = 30$ m/s.
* Confirms the PID tuning is accurate for following a lead vehicle.
*  Demonstrates the system handling non-linear drag while maintaining a safe distance.

### 2. High-Speed Highway Test
* Increasing speed to highway levels (e.g., $V = 40$ m/s).
* Evaluates the controller under high-stress conditions.
* Observes how aerodynamic drag ($F_{drag}$) affects the PID's ability to maintain a gap at high velocities.

### 3. Road Grade Disturbance (The Hill)
* Driving the ego vehicle on a hill while the lead car is on flat ground.
* Tests **Disturbance Rejection** against gravity.
* Proves the Integral ($I$) term compensates for $F_{g}$ to keep the car at the correct distance.



### 4. User Intent: Traditional Cruise Toggle
* **Scenario**: Using a manual switch to bypass the ACC logic.
* **Purpose**: Allows the user to switch from "Safe Distance" to "Fixed Speed" mode.
* **Physics**: The PID ignores the lead vehicle signal and focuses purely on $V_{set}$.
