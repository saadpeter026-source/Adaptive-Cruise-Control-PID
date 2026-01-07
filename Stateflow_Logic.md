# Subsystem 1: Stateflow Logic:
<img width="1325" height="849" alt="image" src="https://github.com/user-attachments/assets/efbbe2d8-0747-4357-8e1a-e1225c5c8a32" />

## State Descriptions
SET: This state initializes the system by setting the target_speed and stored_speed to 30 units while capturing the current vehicle velocity in memory.
Accelerate (Accel): While the button (btn == 2) is held, the system performs a "During" action to increase the target_speed by 0.05 units per time step.

Decelerate (Deccel): While the button (btn == 3) is held, the system performs a "During" action to reduce the target_speed by 0.05 units per time step.

Resume: This state resets the target_speed to the stored_speed previously saved in memory when the resume button (btn == 4) is pressed.

OFF / Cancel: The system enters this state to set the target_speed and active_flag to 0, effectively disabling the cruise control.

Safety: The transition to the OFF state has a [brake == 1] condition, ensuring the brake signal always has priority to shut down the system.
