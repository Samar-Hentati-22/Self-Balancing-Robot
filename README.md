# Self-Balancing Robot/ Inverted Wheeled Pendulum
## A. System Description
A self-balancing robot is a two-wheeled mobile robot that maintains its upright position using sensors and control algorithms, based on the principles of a wheeled inverted pendulum system.
## B. Challenge
Unlike many other systems where stability is achieved by minimizing deviations from a stable equilibrium point, the two-wheeled inverted pendulum system requires maintaining an unstable equilibrium. This makes control even more delicate and demanding
So , How did we determine the system's instability?
## C. Theoretical Study 
### Mathematical Representation

<img width="576" height="292" alt="image" src="https://github.com/user-attachments/assets/e0d26fa2-3ae8-4c4d-864e-a8d2961cca47" />

These are a few system parameters and variables:

- **r**: Wheel radius  
- **2b**: Lateral distance between the two wheels  
- **θ**: Tilt angle of the pendulum body  
- **ψ**: Average wheel rotation angle (psi_r + psi_l)/2  
- **φ**: Yaw angle of the system  

### Made hypotheses
- The two wheels have the same radius and mass.
- The wheels are not deformable.
- The wheels roll on the ground without slipping.
- The ground is a surface with a certain slope.

### Steps to determine the system's dynamic model
1- the expression of the potential energy p and kinetic energy k.

<img width="213" height="92" alt="image" src="https://github.com/user-attachments/assets/4b0330d9-83d4-43f7-b6a7-351aa9384134" />

2-The expression of the lagrangian L = k -  P.

<img width="134" height="80" alt="image" src="https://github.com/user-attachments/assets/f5293a09-8661-43ee-a813-4d0ad9f0a961" />

3-the elaboration of the three equations from the lagrange equation With : 
u: motor couple vector 
f: vector of forces applied to the prismatic joints

4-The simplification of the equations.

### Steps to determine the system's equilibrium points 
1- At equilibrium, all derivatives of the system’s state variables are equal to zero: 

θ̇ = φ̇ = θ̈ = φ̈ = ψ̇ = 0

2- Applying These Conditions:
By applying these equilibrium conditions to the system’s nonlinear dynamic model, and assuming that the control inputs are zero:

uᵣ = uₗ = 0

3- After substituting these conditions, the linearized form of the model becomes:

θ̇ = φ̇ = θ̈ = φ̈ = ψ̇ = 0

A₄ sin(θ) = 0

4-From the above equation, the system’s equilibrium points are obtained when:

θ = 0° or θ = 180°


Thus, the robot can be in two equilibrium configurations:
- **Upright position** → θ = 0° (unstable equilibrium)  
- **Inverted position** → θ = 180° (stable when lying down)

### The use of PID 
To stabilize the system around its upright equilibrium point (θ = 0°), a PID (Proportional–Integral–Derivative) controller is implemented.
#### Objective 
The main goal of the PID controller is to:
- Maintain the pendulum in the upright position by minimizing the angular deviation θ.  
- Control the wheel rotation ψ to ensure balance and position stability.
#### Control Law 
The control input applied to each motor is defined as:

u(t) = Kp * e(t) + Ki * ∫e(t)dt + Kd * de(t)/dt

where:  
- e(t) = reference angle − measured angle (θ_ref − θ)  
- Kp = proportional gain  
- Ki = integral gain  
- Kd = derivative gain  

#### Controller Roles
- **Proportional term (Kp):** Reacts to the current error, providing immediate correction.  
- **Integral term (Ki):** Eliminates steady-state error over time.  
- **Derivative term (Kd):** Predicts future error behavior to reduce overshoot and oscillations.  

#### Implementation
Each wheel motor is controlled independently, but both are coordinated to maintain:
- Angular stability (θ), ensuring the pendulum remains upright.  
- Position control (φ), keeping the robot balanced and centered.

#### Tuning
The PID parameters were tuned experimentally to achieve:
- Fast response  
- Minimal overshoot  
- Stable steady-state behavior  
