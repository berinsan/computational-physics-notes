# Runge-Kutta 4 (RK4)
This method is quite similar to RK2, but this time the slope used to estimate y(t) is a weighted average of the slopes at the beginning, middle and the end of the time step, which gives a more accurate estimate for the average slope over that time step. This method is called fourth-order because the global error scales as ```h⁴```, which is an improvement from Euler’s method and RK2.

The recursive algorithm:
<pre>
    Estimate the slope at current point:
    k1 = f(yₙ, tₙ)

    Estimate slope at mid point:
    k2 = f(yₙ + k1 * h/2, tₙ + h/2)
    
    Estimate slope at mid point using k2:
    k3 = f(yₙ + k2 * h/2, tₙ + h/2)

    Estimate slope at end point using k3:
    k4 = f(yₙ + k3 * h, tₙ + h)

    Estimate y at end point using the weighted average of slopes:
    yₙ₊₁ = yₙ + (h/6) * (k1 + 2*k2 + 2*k3 + k4)
</pre>

