# Problem 1

## Investigating the Range as a Function of the Angle of Projection

### Theoretical Foundation
Projectile motion follows the equations of kinematics. The range $R$ of a projectile launched at an initial speed $v_0$ and an angle $\theta$ is given by:

$$ R = \frac{v_0^2 \sin(2\theta)}{g} $$

where:
- $v_0$ is the initial velocity,
- $g$ is the gravitational acceleration,
- $\theta$ is the angle of projection.

The maximum range occurs at $\theta = 45^\circ$, as $\sin(2\theta)$ reaches its maximum value of 1.

### Analysis of the Range
The range depends on multiple factors:
1. **Angle of Projection**: The function $\sin(2\theta)$ dictates a symmetric relationship between angles on either side of $45^\circ$.
2. **Initial Velocity**: Since $R \propto v_0^2$, increasing $v_0$ leads to a quadratic increase in range.
3. **Gravity**: Higher gravity decreases range, as $R \propto \frac{1}{g}$.

Below is a Python simulation to visualize this relationship.

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(theta: np.ndarray, v0: float, g: float) -> np.ndarray:
    """Compute the range of a projectile for an array of angles."""
    theta_rad = np.radians(theta)
    return (v0**2 * np.sin(2 * theta_rad)) / g

# Parameters
v0_values = [20, 50, 80]  # Different initial velocities (m/s)
g = 9.81  # Gravitational acceleration (m/s^2)
angles = np.linspace(0, 90, 100)  # Angle range from 0 to 90 degrees

fig_size = (8, 5)  # Adjustable figure size
plt.figure(figsize=fig_size)
for v0 in v0_values:
    ranges = projectile_range(angles, v0, g)  # Use vectorized NumPy function
    plt.plot(angles, ranges, label=f'$v_0 = {v0}$ m/s')

plt.xlabel("Angle of Projection (degrees)")
plt.ylabel("Range (meters)")
plt.title("Projectile Range as a Function of Angle")
plt.legend()
plt.grid()
plt.show()
```

### Practical Applications
This model applies to various real-world scenarios, including:
- **Ballistics**: Optimizing the angle for maximum range in artillery.
- **Sports**: Understanding projectile motion in soccer, basketball, or golf.
- **Engineering**: Designing optimal launch angles for drones or water jets.
- **Space Science**: Planning rocket launches where gravity varies with altitude.

### Advanced Considerations
1. **Air Resistance**:
   - The presence of drag modifies the trajectory and reduces range.
   - A numerical approach is required to include aerodynamic effects.
   
2. **Variable Gravity**:
   - For large-scale motion, $g$ is not constant and depends on altitude.
   - This is crucial for space launches and astrophysics.

3. **Uneven Terrain**:
   - In real scenarios, the landing surface may not be at the same height as the launch point.
   - Adjustments to the equations can accommodate different landing heights.

### Conclusion
Projectile motion offers a rich mathematical framework with extensive real-world applications. By studying its governing equations, we gain insights applicable to multiple fields, from sports science to aerospace engineering. Extensions of this model can incorporate realistic effects such as drag and varying gravitational forces, making it a versatile and practical tool in physics and engineering.
