# Magnetic Levitation System Modeling
> <picture>
>   <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Mqxx/GitHub-Markdown/main/blockquotes/badge/light-theme/info.svg">
>   <img alt="Info" src="https://raw.githubusercontent.com/Mqxx/GitHub-Markdown/main/blockquotes/badge/dark-theme/info.svg">
> </picture><br>
>
> Check the branches!
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

The **linearization** around **y<sub>d</sub>** as the **setpoint** is accomplished with the following result.

<img src="/readme_images/linearization.PNG">

The **open-loop** transfer function is obtained by assuming y<sub>d</sub> = 0.306[m] and following this procedure.
<img src="/readme_images/transfer_func.PNG">

And the **closed-loop** transfer function with a **negative unit feedback** is written as follows.
<img src="/readme_images/closed.PNG">

The **root locus** diagram of the given closed-loop transfer function is displayed below. However, since the diagram lies on the right side of the imaginary axis, it indicates **instability**.

<img src="/readme_images/rlocus1.PNG">

Please find the zoomed version of the root locus diagram displayed below.

<img src="/readme_images/zoom.PNG">

To stabilize this system, a **PID controller** is designed with the following desired attributes for a **step input**:

1. The maximum **step response** should be within 2 seconds.
2. The **steady-state error** should be zero.
3. The **settling time** should not exceed 2 seconds.
4. The maximum **overshoot** should be limited to 35%.

The PID controller: $G_c = \frac{6.046(s + 4)(s + 6)}{s}$

After incorporating the PID controller into the system, its behavior is depicted as follows:

| Root Locus | Step Response | Step Info |
| --- | --- | --- |
| <img src="/readme_images/rlocus2.jpg"> | <img src="/readme_images/step.jpg"> | <img src="/readme_images/info.jpg"> |

Now this controller is added to the main **non-linear** system and its ability to control it is as follows.

<img src="/readme_images/3d.gif" width="500" height="500">

## [Frequency_Analysis](https://github.com/fardinabbasi/Electromagnetic_Levitation_System_Modeling/tree/Frequency_Analysis)
The **state space** is depicted below.

<img src="/readme_images/state_space.PNG">

The **linearization** around **y<sub>d</sub>** as the **setpoint** is accomplished with the following result.

<img src="/readme_images/linearization.PNG">

The **open-loop** transfer function is obtained by assuming y<sub>d</sub> = 0.306[m] and following this procedure.
<img src="/readme_images/transfer_func.PNG">

The **Bode** and **Nyquist** diagrams of this uncontrolled system are depicted below.

| Bode | Nyquist |
| --- | --- |
| <img src="/readme_images/bode1.jpg"> | <img src="/readme_images/nyquist.jpg"> |

The following conclusions can be drawn from the provided diagrams:
1. As the magnitude never reaches 0 dB, the **phase margin** is considered to be infinite.
2. The **gain margin** can be calculated as $k=\frac{1}{G(0)}$.
3. At a frequency of 3 Hz, the gain decreases by 3 dB, indicating a **bandwidth** of 3 Hz.
4. The system is unstable according to the **Nyquist Stability Criterion** because there is a pole in the right half of the imaginary axis and N=0, violating the condition $Z=N+P=0$.

To stabilize this system, a **PI controller** is designed with the following desired attributes for a **step input**:

1. The maximum **step response** should be within 2 seconds.
2. The **steady-state error** should be zero.
3. The maximum **overshoot** should be limited to 35%.
The PI controller: $G_c = \frac{(s + 2.371)}{s}$

| Nyquist | Bode | Step Response | Step Info |
| --- | --- | --- | --- |
| <img src="/readme_images/nyquist2.jpg"> | <img src="/readme_images/bode4.jpg"> | <img src="/readme_images/step_responcef.jpg"> | <img src="/readme_images/info2.PNG"> |

The system satisfies the **Nyquist Stability Criterion** as it possesses a pole in the right half of the imaginary axis, and N equals -1, meeting the condition $Z = N + P = 0$, thus establishing stability.

Furthermore, the system currently exhibits a **phase margin** of approximately 50 degrees.
