# Euler's Method
Imagine you don't have an explicit formula for the motion you're describing. You know only the initial conditions (position and velocity) and the forces at play. 
(If you know the force and the mass of the object, you also know the acceleration.)

Using a time step ```h```, we calculate the position and velocity of the object after a time step ```h``` has passed.

**For example, consider:**
```python
x₀ = 0
v₀ = 0
a = const.
```

We calculate the position and velocity after one time step using the initial velocity, initial position, and acceleration. Assuming velocity is approximately constant through a small time step, we find the position after one time step as:

**Position after one time step:**
```python
x₁ = x₀ + v₀ * h
```

**Velocity after one time step:**
```python
v₁ = v₀ + a * h
  ```

Now the position after one time step is x₁, and the velocity is v₁.

**We repeat:**
```python
x₂ = x₁ + v₁ * h  
v₂ = v₁ + a * h
```

Essentially, at every step, position and velocity are approximated by using the first two terms in the Taylor expansion of their exact formulas.

Things to Note:
* With this method, the main source of error comes from the approximation of a constant velocity during each time step. Over time, the error accumulates and grows larger.

* The asymmetrical use of information between time steps (we use only the initial velocity to calculate position after one time step, ignoring the change in velocity during that step) also contributes to the error.

Applying this to projectile motion:
```python
import matplotlib.pyplot as plt

g = 9.8 # gravity
y = 0.0 # initial position
v0 = 5.0 # initial velocity
ta = [] # time array for plotting
ya = [] # position array for plotting
t = 0.0 # time
h = 0.02 # step size
yb = [] # holds analytic solution

while t<1.0:
    ta.append(t)
    ya.append(y)
    yb. append(v0*t-g*t*t/2.0) # analytic solution
    v = v0 - g*t # calculate v(t)
    y = y + v*h # Euler's method
    t = t + h

plt.figure() # start a figure
plt.plot(ta, ya, ta, yb, '--') # draw 2nd curve as dashed
plt.xlabel('t (s)')
plt.ylabel('y (m)')
plt.show()
```
