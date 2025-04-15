# Problem Great project! The forced damped pendulum is a classic system that opens up so many fascinating directions, from resonance to chaos theory.

To get you started, here’s a structured plan you can follow for your report and Python notebook:

---

## 📘 Markdown Document Structure

### **1. Theoretical Foundation**

#### 📌 Governing Equation:
The equation of motion for a forced damped pendulum is:

\[
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \sin(\theta) = A \cos(\omega t)
\]

Where:
- \(\theta\) = angular displacement
- \(\gamma\) = damping coefficient
- \(\omega_0 = \sqrt{g/L}\) = natural frequency
- \(A\) = driving amplitude
- \(\omega\) = driving frequency

#### 🧠 Small-Angle Approximation:
For small angles, \(\sin(\theta) \approx \theta\):

\[
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = A \cos(\omega t)
\]

Solve this using methods for linear ODEs (e.g., undetermined coefficients or Laplace transforms) and identify resonance conditions when \(\omega \approx \omega_0\).

---

### **2. Analysis of Dynamics**

- Use simulations to explore how varying:
  - \(\gamma\) (damping)
  - \(A\) (amplitude)
  - \(\omega\) (driving frequency)
  affect motion.

- Discuss:
  - Regular periodic motion
  - Quasiperiodicity
  - Onset of chaos (e.g., using Lyapunov exponents or visual markers)

---

### **3. Practical Applications**

Relate the pendulum to:
- Energy harvesting systems (resonant-based harvesting)
- Suspension bridges (resonance-related failures)
- Driven RLC circuits (electrical analog)

---

### **4. Computational Model (Python)**

Include:
- Numerical solver (e.g., `scipy.integrate.solve_ivp`)
- Time series and phase space plots
- Poincaré sections: sample the state at regular intervals
- Bifurcation diagram: sweep parameters and plot long-term behavior

---

## 🐍 Python Code Outline

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Pendulum parameters
gamma = 0.2     # Damping coefficient
omega_0 = 1.0   # Natural frequency
A = 1.2         # Driving force amplitude
omega = 2/3     # Driving frequency

# ODE system
def pendulum(t, y):
    theta, omega_p = y
    dtheta_dt = omega_p
    domega_dt = -gamma * omega_p - omega_0**2 * np.sin(theta) + A * np.cos(omega * t)
    return [dtheta_dt, domega_dt]

# Initial conditions and time span
y0 = [0.1, 0.0]
t_span = (0, 100)
t_eval = np.linspace(*t_span, 10000)

# Solve ODE
sol = solve_ivp(pendulum, t_span, y0, t_eval=t_eval)

# Plotting
plt.plot(sol.t, sol.y[0])
plt.xlabel('Time')
plt.ylabel('Theta (rad)')
plt.title('Forced Damped Pendulum Motion')
plt.grid(True)
plt.show()
```

From here, you can:
- Add sliders for interactive control (e.g., with `ipywidgets`)
- Generate Poincaré sections: `theta` and `omega` sampled at integer multiples of driving period \( T = \frac{2\pi}{\omega} \)
- Create bifurcation plots by sweeping `A` or `omega`

---

h