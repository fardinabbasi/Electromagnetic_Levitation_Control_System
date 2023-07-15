# Magnetic Levitation System Modeling
## Introduction
Magnetic levitation is a remarkable technique that utilizes the power of magnetic fields to defy gravity and suspend objects in mid-air. A prominent illustration of its practical implementation is the maglev train, which capitalizes on this levitating effect to minimize friction and achieve remarkable speeds.

<img src="/readme_images/train.PNG">
The magnetic levitation system is represented by the understudied system depicted below.

<img src="/readme_images/levitation_system.jpg">
By analyzing the aforementioned system, the equations are written as follows.
<img src="/readme_images/equations.PNG">

| R | L | g | c | M | f<sub>v</sub> |
| --- | --- | --- | ---| --- | --- |
| $5[&Omega;]$ | $0.02[H]$ | $9.84  [\frac{m}{s^2}]$ | $0.3 [\frac{N \cdot m}{A^2}]$ | $106[g]$ | $0.02[\frac{N \cdot s}{m}]$ |

## [Time Analysis](https://github.com/fardinabbasi/Electromagnetic_Levitation_System_Modeling/tree/Time_Analysis)
The **state space** is depicted below.

<img src="/readme_images/state_space.PNG">

The **linearization** around **y<sub>d</sub>** as the **setpoint** is accomplished using the following result.

<img src="/readme_images/linearization.PNG">

The **open-loop** transfer function is obtained by assuming y<sub>d</sub> = 0.306[m] and following this procedure.
<img src="/readme_images/transfer_func.PNG">

And the **closed-loop** transfer function with a **negative unit feedback** is written as follows.
<img src="/readme_images/closed.PNG">

The **root locus** diagram of the given closed-loop transfer function is displayed below. However, since the diagram lies on the right side of the imaginary axis, it indicates **instability**.

<img src="/readme_images/rlocus1.PNG">

Please find the zoomed version of the root locus diagram displayed below.
<img src="/readme_images/zoom.PNG">
