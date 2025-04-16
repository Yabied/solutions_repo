# Problem 1# Kepler's Third Law Simulation and Analysis

import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # gravitational constant in m^3 kg^-1 s^-2
M_sun = 1.989e30  # mass of the Sun in kg

# Function to calculate orbital period given radius (circular orbit)
def orbital_period(radius, mass=M_sun):
    return 2 * np.pi * np.sqrt(radius**3 / (G * mass))

# Generate a range of orbital radii (in meters)
radii = np.linspace(0.3, 30, 100) * 1.496e11  # AU to meters
periods = orbital_period(radii)

# Plot T^2 vs R^3 to verify linearity
T_squared = periods**2
R_cubed = radii**3

plt.figure(figsize=(8, 6))
plt.plot(R_cubed, T_squared, label=r"$T^2$ vs $R^3$")
plt.xlabel(r"$R^3$ (m^3)")
plt.ylabel(r"$T^2$ (s^2)")
plt.title("Verification of Kepler's Third Law")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()

# Real-world example: Moon around Earth
M_earth = 5.972e24  # kg
r_moon = 384400e3  # meters
T_moon = orbital_period(r_moon, M_earth)
print(f"Orbital period of the Moon: {T_moon / 86400:.2f} days")

# Additional: Comparing planetary orbits in the Solar System
planet_data = {
    'Mercury': (0.39, 88),
    'Venus': (0.72, 225),
    'Earth': (1.00, 365.25),
    'Mars': (1.52, 687),
    'Jupiter': (5.20, 4333),
    'Saturn': (9.58, 10759),
    'Uranus': (19.20, 30687),
    'Neptune': (30.05, 60190)
}

r_au = np.array([planet_data[p][0] for p in planet_data])
t_days = np.array([planet_data[p][1] for p in planet_data])

plt.figure(figsize=(8, 6))
plt.plot(r_au**3, t_days**2, 'o-', label='Planets')
plt.xlabel(r"$R^3$ (AU^3)")
plt.ylabel(r"$T^2$ (days^2)")
plt.title("Kepler's Third Law for Planets")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
