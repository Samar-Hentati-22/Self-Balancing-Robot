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





