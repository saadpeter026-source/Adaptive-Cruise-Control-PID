# Subsystem 3 (Plant/Ego Vehicle)

<img width="839" height="597" alt="image" src="https://github.com/user-attachments/assets/701d0c10-7d95-4786-90ed-1b0df4345c1f" />

## Physical Representation (FBD)
* $u$ : Engine Force (Control Input)
* $F_{drag}$ : Aerodynamic Drag
* $F_{g}$ : Force due to road grade (gravity)
* $F_{N}$ : Normal Force
* $W$ : Vehicle Weight ($m \cdot g$)

## Mathematical Equation

The longitudinal motion of the vehicle is governed by Newton's Second Law, which states that the sum of forces equals mass times acceleration.

$$\sum F = u - F_{drag} - F_{g}$$
$$ma = u - F_{drag} - F_{g}$$

**Where:**
* $u$ : Control Input Force (Engine Force)
* $F_{drag} = k \cdot v^2$ : Aerodynamic Drag
* $F_{g} = m \cdot g \cdot \sin(\theta)$ : Force due to road grade (gravity)

**The Drag Constant ($k$):**
In this model, the constant $k$ represents the physical properties of the vehicle and environment:
$$k = \frac{1}{2} \cdot \rho \cdot C_{d} \cdot A$$
* $\rho$ : Air Density
* $C_{d}$ : Drag Coefficient
* $A$ : Frontal Surface Area

---

**Full Vehicle Dynamic Equation:**
$$m \cdot a = u - (k \cdot v^2) - (m \cdot g \cdot \sin(\theta))$$

**Final Acceleration Equation:**
This equation is implemented in the Simulink plant using the $1/m$ gain block to solve for the system's acceleration:
$$a = \frac{1}{m} (u - (k \cdot v^2) - (m \cdot g \cdot \sin(\theta)))$$

## Simulink Implementation
<img width="1326" height="664" alt="image" src="https://github.com/user-attachments/assets/30e6541e-d27c-4e32-b107-10d07ec1b5cd" />
Using the same equaiton of accelraiton from above, we can model the subsystem by using simuslink blocks....
