# Subsystem 1: Stateflow Logic:
<img width="1325" height="849" alt="image" src="https://github.com/user-attachments/assets/efbbe2d8-0747-4357-8e1a-e1225c5c8a32" />

## Overview

### State Descriptions

| State / Logic | Description |
| :--- | :--- |
| **SET** | This state initializes the system by setting the `target_speed` and `stored_speed` to $30$ m/s while capturing the current vehicle velocity in memory. |
| **Accelerate (Accel)** |  While the button ($btn == 2$) is held, the system performs a "During" action to increase the `target_speed` by $0.05$ units per time step. |
| **Decelerate (Deccel)** | While the button ($btn == 3$) is held, the system performs a "During" action to reduce the `target_speed` by $0.05$ units per time step. |
| **Resume** | This state resets the `target_speed` to the `stored_speed` previously saved in memory when the resume button ($btn == 4$) is pressed. |
| **OFF / Cancel** | The system enters this state to set the `target_speed` and `active_flag` to $0$, effectively disabling the cruise control. |
| **Safety** | The transition to the OFF state has a $[brake == 1]$ condition, ensuring the brake signal always has priority to shut down the system. |

### Control Input Mapping (btn)

The following table defines the specific input values used to trigger state transitions within the Stateflow logic:

| Value | Action | Description |
| :---: | :--- | :--- |
| $0$ | **Idle / Release** | Returns the system to the **SET** state; stops active speed adjustment. |
| $1$ | **Set / Initialize** | Transitions the system from **OFF** to **ON\_MODE**. |
| $2$ | **Accelerate** | Triggers the **Accel** state to increment the `target_speed`. |
| $3$ | **Decelerate** | Triggers the **Decel** state to decrement the `target_speed`. |
| $4$ | **Resume** | Transitions to the **Resume** state to restore the previously `stored_speed`. |

### Brake Signal Mapping

The brake input acts as a high-priority safety override or emergency brake for the entire ACC system.

| Value | Meaning | System Behavior |
| :---: | :--- | :--- |
| $0$ | **Brake Released** | System is allowed to operate in **ON\_MODE**. |
| $1$ | **Brake Pressed** | Forces an immediate transition to the **OFF** state. |
