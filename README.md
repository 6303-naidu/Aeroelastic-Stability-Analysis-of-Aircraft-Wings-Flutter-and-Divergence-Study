# Aeroelastic Stability and Flutter Analysis Project

## Project Overview

This project focuses on the numerical analysis of aeroelastic phenomena in aircraft wing structures, primarily flutter and divergence instabilities. Using Python, the project systematically models coupled plunge and pitch dynamics, structural and aerodynamic matrices, and performs eigenvalue-based stability assessments under varying flight conditions. The analysis incorporates effects of speed, Mach number, sweep angle, stiffness, and aerodynamic control parameters to predict critical speeds and guide aerospace structural design.

---

## Contents

The project consists of seven Python scripts, each focusing on a specific aspect of aeroelastic and aerodynamic analysis:

1. **_oscillatory_response**  
   *Simulates time-domain oscillatory response of wing plunge and pitch motions at fixed airspeeds to illustrate dynamic behavior.*

2. **Divergence speed vs sweep_angles vs varying mach numbers**  
   *Computes divergence speeds as a function of sweep angle and Mach number, addressing static aeroelastic instability.*

3. **flutter_airspeed**  
   *Performs flutter speed analysis by sweeping airspeed and solving eigenvalue problems to detect dynamic instability boundaries.*

4. **goland_flutter**  
   *Conducts flutter analysis on the Goland wing model, accounting for sweep angles and structural parameters in a realistic scenario.*

5. **flutter_divergence_models**  
   *Compares different flutter and divergence analysis methods and models, highlighting effects of aerodynamic and structural components.*

6. **Mach Number Effects on Aerodynamic Load Parameter**  
   *Explores the influence of Mach number on an aerodynamic load coefficient (q_R), demonstrating compressibility effects.*

7. **Efficiency Parameter (η) vs. Control Parameter (Q) Across Sweep Angles**  
   *Plots efficiency parameter (η) versus control parameter (Q) for multiple sweep angles, assisting in aerodynamic performance evaluation.*

---

## Project Structure & Usage

- Each script is modular and can be run independently to observe corresponding results.
- Dependencies: Python 3.8+, with `numpy`, `scipy`, and `matplotlib` libraries installed.
- Run scripts via command line or in a Jupyter notebook environment to generate plots and outputs that illustrate aerodynamic and structural stability characteristics.
- Visualization includes displacement responses, eigenvalue real parts, divergence speeds, flutter boundaries, and parametric studies relevant for design.

---

## How to Run

1. Install dependencies (if not installed):

pip install numpy scipy matplotlib

text

2. Execute any script, e.g.:
import numpy as np
import matplotlib.pyplot as plt

Kt = 1.2
Clbeta0 = 0.05
Cldelta0 = 0.08
Cmacbeta0 = 0.03
Cmacdelta0 = 0.04
Clalpha0 = 5.7
beta = 2*np.pi/180
delta = 3*np.pi/180
s = 20
e1 = 0.9
e2 = 1.1
e3 = 0.7
c = 3
M = np.linspace(0.1, 0.7, 50)
qR = np.zeros_like(M)

for i, mach in enumerate(M):
    numerator = Kt * (Clbeta0 * beta + Cldelta0 * delta)
    denominator1 = s * Clbeta0 * (e1 * (Clalpha0 / np.sqrt(1 - mach ** 2)) + e2) * beta
    denominator2 = s * Cldelta0 * (e1 * (Clalpha0 / np.sqrt(1 - mach ** 2)) - e3) * delta
    denominator3 = s * c * (Cmacbeta0 * beta + Cmacdelta0 * delta)
    qR[i] = numerator / (denominator1 + denominator2 - denominator3)

plt.figure()
plt.plot(M, qR, 'b', linewidth=2)
plt.xlabel('Mach number (M)')
plt.ylabel('q_R')
plt.title('Variation of q_R with Mach number')
plt.grid(True)
plt.show()
   



text

3. View generated plots and analyze flutter and divergence characteristics.

---

## Project Significance

This suite supports aerospace engineers in:

- Modeling complex aeroelastic interactions for structural safety assessments.
- Identifying critical flutter and divergence speeds for wing designs.
- Evaluating aerodynamic parameters’ sensitivity to speed, Mach number, and geometry.
- Enhancing design decisions through detailed parametric analysis and visualization.

---

## Author

[Varri Appalanaidu]  
Aerospace Engineering  
[https://github.com/6303-naidu/Aeroelastic-Stability-Analysis-of-Aircraft-Wings-Flutter-and-Divergence-Study]

---

## References

- Classic Aeroelasticity and Flutter textbooks and papers.
- Scientific Python documentation for numerical methods and plotting.
