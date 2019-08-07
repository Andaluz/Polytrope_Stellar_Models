# Polytrope Stellar Models
## Daniel D. Andaluz

Use the 4th-order Runge-Kutta integration method to find solutions for polytrope indecies using the Lane-Emden ODE.

### Lane-Emden polytrope equation

\begin{align*} \frac{1}{\xi^2}\frac{d}{d\xi}(\xi^2\frac{d\theta}{d\xi}) = -\theta^n \end{align*}

We can rewrite this as 2 first order equations:

\begin{align*} \frac{dy}{d\xi} = z \end{align*}
\begin{align*} \frac{dz}{d\xi} = -\frac{2}{\xi}z-y^n \end{align*}

For a given polytrope index n, the main class will integrate the system for us. When ploting the results, we can obtain the parameter $\xi_1$

Here, $\xi_1$ is our stellar radius. We will estimate the radius each step while ensuring that the next step does not take us past that estimate. This will prevent us from obtaining negative $\theta$ values. Given a point $(\xi_0,y_0)$, and the derivative at that point, $z_0 = \frac{dy}{d\xi}\Big|_{\xi_0}$, we can write the following equation of a line:

\begin{align*} y(\xi)-y_0 = z_0(\xi-\xi_0) \end{align*}

$\xi_1$ is defined to be our estimated stellar radius when y becomes zero. Thus:

\begin{align*} \xi = -\frac{y_0}{z_0}+\xi_0 \end{align*}

However, we must make sure that our stepsize $\Delta\xi$ is small enough that we do not go beyond this estimate.
