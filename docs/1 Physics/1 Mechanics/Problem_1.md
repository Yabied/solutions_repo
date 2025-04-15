# Problem 1

# Investigating the Range as a Function of the Angle of Projection



## Motivation


Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Yet, beneath this simplicity lies a complex and versatile framework. The equations governing projectile motion involve both linear and quadratic relationships, making them accessible yet deeply insightful.

What makes this topic particularly compelling is the number of free parameters involved in these equations, such as initial velocity, gravitational acceleration, and launch height. These parameters give rise to a diverse set of solutions that can describe a wide array of real-world phenomena, from the arc of a soccer ball to the trajectory of a rocket.

## Task

### 1. Theoretical Foundation


- Begin by deriving the governing equations of motion from fundamental principles. This involves solving a basic differential equation to establish the general form of the motion.
- Highlight how variations in initial conditions lead to a family of solutions.

The horizontal and vertical components of motion can be expressed as:

$$x(t) = v_0 \cos(\theta) t $$


$$y(t) = v_0 \sin(\theta) t - \frac{1}{2} g t^2 $$

where:
- $v_0 $ is the initial velocity,

- $\theta $ is the angle of projection,

- $g $ is the acceleration due to gravity.


The time of flight is obtained by solving for when $y = 0 $:

$$t_f = \frac{2 v_0 \sin(\theta)}{g} $$


The range is given by:

$$R = v_0 \cos(\theta) \times t_f = \frac{v_0^2 \sin(2\theta)}{g} $$



### 2. Analysis of the Range


- Investigate how the horizontal range depends on the angle of projection.


- Discuss how changes in other parameters, such as initial velocity and gravitational acceleration, influence the relationship.


Observations:

- The range is maximized when $\theta = 45^\circ $.

- Increasing $v_0 $ results in a larger range.

- Increasing $g $ reduces the range.


### 3. Practical Applications


- Reflect on how this model can be adapted to describe various real-world situations, such as projectiles launched on uneven terrain or in the presence of air resistance.

- Consider the effect of wind resistance and varying gravity, such as on different planets or celestial bodies.



### 4. Implementation


- Develop a computational tool or algorithm to simulate projectile motion.

- Visualize the range as a function of the angle of projection for different sets of initial conditions.


A simple Python implementation using matplotlib and numpy can be used to generate plots demonstrating these principles.

```python
import numpy as np
import matplotlib.pyplot as plt

g = 9.81  # gravitational acceleration (m/s^2)
v0 = 20  # initial velocity (m/s)
angles = np.linspace(0, 90, 100)  # angles from 0 to 90 degrees
ranges = (v0**2 * np.sin(np.radians(2*angles))) / g

plt.plot(angles, ranges)
plt.xlabel("Angle of Projection (degrees)")
plt.ylabel("Range (m)")
plt.title("Projectile Range as a Function of Angle")
plt.grid()
plt.show()
```

This simulation can be extended to account for varying initial conditions and external factors such as air resistance.

## Conclusion
By systematically analyzing the relationship between the angle of projection and the range of a projectile, we uncover key insights that are not only fundamental to physics but also widely applicable in engineering, sports science, and aerospace technology. Computational modeling further enhances our ability to visualize and understand these relationships, providing a powerful tool for both theoretical and practical applications.
that


