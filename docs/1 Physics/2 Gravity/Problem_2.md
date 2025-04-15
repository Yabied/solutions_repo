# Problem 2Great! Here's how we can structure your Markdown document and Python notebook to cover everything:

---

## 📄 **Escape Velocities and Cosmic Velocities**

### 🚀 Motivation
Escape and cosmic velocities form the foundation of astrodynamics and space mission planning. They determine the energy required to overcome gravitational bounds, whether to maintain orbit, leave a planet, or even escape a solar system.

---

### 🌌 Definitions

#### 1. **First Cosmic Velocity** (Orbital Velocity)
- Minimum velocity needed to stay in a stable circular orbit just above a celestial body’s surface.
- $ v_1 = \sqrt{\frac{GM}{R}} \)

#### 2. **Second Cosmic Velocity** (Escape Velocity)
- Minimum velocity to completely escape the gravitational field without further propulsion.
- $ v_2 = \sqrt{2GM/R} \)

#### 3. **Third Cosmic Velocity** (Solar System Escape Velocity)
- Minimum velocity to escape the gravitational influence of the Sun (or central star) from a planet’s orbit.
- Requires considering both the planet’s orbital speed and the Sun’s pull.

---

### 🧮 Mathematical Derivations
Let:
- $ G \) = gravitational constant
- $ M \) = mass of the celestial body
- $ R \) = radius from center of mass

**Key Insight**:
- $ v_2 = \sqrt{2} \cdot v_1 \)
- $ v_3 \) is derived from energy conservation involving both planet and solar system dynamics.

---

### 🌍 Comparative Calculations

We'll calculate and visualize the three velocities for:

- Earth
- Mars
- Jupiter

#### Python Snippet Preview:
```python
import matplotlib.pyplot as plt
import numpy as np

# Constants
G = 6.67430e-11  # m³/kg/s²

# Celestial bodies data: [mass (kg), radius (m), orbital radius (m) around Sun]
bodies = {
    'Earth': [5.972e24, 6.371e6, 1.496e11],
    'Mars': [6.417e23, 3.390e6, 2.279e11],
    'Jupiter': [1.898e27, 6.9911e7, 7.785e11]
}

def velocities(mass, radius, orbit_radius):
    v1 = np.sqrt(G * mass / radius)
    v2 = np.sqrt(2 * G * mass / radius)
    v_orbit_sun = np.sqrt(G * 1.989e30 / orbit_radius)  # Sun mass = 1.989e30 kg
    v3 = v_orbit_sun + v2
    return v1, v2, v3

results = {body: velocities(*data) for body, data in bodies.items()}

# Visualization
labels = list(results.keys())
v1_vals = [results[b][0] for b in labels]
v2_vals = [results[b][1] for b in labels]
v3_vals = [results[b][2] for b in labels]

x = np.arange(len(labels))
width = 0.25

plt.figure(figsize=(10, 6))
plt.bar(x - width, v1_vals, width, label='1st Cosmic Velocity')
plt.bar(x, v2_vals, width, label='2nd Cosmic Velocity')
plt.bar(x + width, v3_vals, width, label='3rd Cosmic Velocity')
plt.xticks(x, labels)
plt.ylabel('Velocity (m/s)')
plt.title('Cosmic Velocities for Different Planets')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

---

### 🛰️ Application in Space Exploration

- **First Cosmic Velocity**: Used for satellite launches into Earth orbit (LEO, MEO, GEO).
- **Second Cosmic Velocity**: Launching missions like Voyager, Apollo, Mars Rovers.
- **Third Cosmic Velocity**: Needed for leaving the Solar System – critical for interstellar probes.

---

### 📦 Deliverables

You’ll get:
- A Markdown document (`cosmic_velocities.md`)
- A Python notebook (`cosmic_velocities.ipynb`) with:
  - All formulas and derivations
  - Calculations
  - Visualizations

---

