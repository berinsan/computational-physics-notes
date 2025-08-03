# Runge-Kutta 2 (RK2)
Similar to Euler's method, RK2 is  a recursive algorithm used to approximate analytic solutions. However, in this method there is an embedded error correction mechanism.

Instead of using initial velocity, it uses the velocity halfway through the time step to approximate position at the end of a time step, which is a better approximation of the average velocity over that time interval.

```python
v_half = v - g * (h/2)
y = y + v_half * h
v = v - g * h
```
