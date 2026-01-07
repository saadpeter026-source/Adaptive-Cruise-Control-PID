# Subsystem 3 (Plant/Ego Vehicle)

<img width="839" height="597" alt="image" src="https://github.com/user-attachments/assets/701d0c10-7d95-4786-90ed-1b0df4345c1f" />

## Physical Representation (FBD)
* $u$ : Engine Force (Control Input)
* $F_{drag}$ : Aerodynamic Drag
* $F_{g}$ : Force due to road grade (gravity)
* $F_{N}$ : Normal Force
* $W$ : Vehicle Weight ($m \cdot g$)

## Mathematical Equation
$$\sum F = u - F_{drag} - F_{g}$$  $$ma = u - F_{drag} - F_{g}$$
Where $$u = \text{Control Input Force}$$
$$F_{drag} = k \cdot v^2$$
$$F_{g} = m \cdot g \cdot \sin(\theta)$$
Giving us a full vehicle Dynamic equation for the model system
$$m \cdot a = u - (k \cdot v^2) - (m \cdot g \cdot \sin(\theta))$$
Acceleration equation
$$a = \frac{1}{m} (u - (k \cdot v^2) - (m \cdot g \cdot \sin(\theta)))$$
