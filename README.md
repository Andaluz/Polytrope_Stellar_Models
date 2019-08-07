# Polytrope Stellar Models
## Daniel D. Andaluz

Use the 4th-order Runge-Kutta integration method to find solutions for polytrope indecies using the Lane-Emden ODE.

### Lane-Emden polytrope equation

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\begin{align*}&space;\frac{1}{\xi^2}\frac{d}{d\xi}(\xi^2\frac{d\theta}{d\xi})&space;=&space;-\theta^n&space;\end{align*}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\begin{align*}&space;\frac{1}{\xi^2}\frac{d}{d\xi}(\xi^2\frac{d\theta}{d\xi})&space;=&space;-\theta^n&space;\end{align*}" title="\begin{align*} \frac{1}{\xi^2}\frac{d}{d\xi}(\xi^2\frac{d\theta}{d\xi}) = -\theta^n \end{align*}" /></a>

We can rewrite this as 2 first order equations:

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\begin{align*}&space;\frac{dy}{d\xi}&space;=&space;z&space;\end{align*}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\begin{align*}&space;\frac{dy}{d\xi}&space;=&space;z&space;\end{align*}" title="\begin{align*} \frac{dy}{d\xi} = z \end{align*}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\begin{align*}&space;\frac{dz}{d\xi}&space;=&space;-\frac{2}{\xi}z-y^n&space;\end{align*}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\begin{align*}&space;\frac{dz}{d\xi}&space;=&space;-\frac{2}{\xi}z-y^n&space;\end{align*}" title="\begin{align*} \frac{dz}{d\xi} = -\frac{2}{\xi}z-y^n \end{align*}" /></a>

For a given polytrope index n, the main class will integrate the system for us. When plotting the results, we can obtain the parameter <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;$\xi_1$" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;$\xi_1$" title="$\xi_1$" /></a>

Here, <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;$\xi_1$" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;$\xi_1$" title="$\xi_1$" /></a> is our stellar radius. We will estimate the radius each step while ensuring that the next step does not take us past that estimate. This will prevent us from obtaining negative <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;$\theta$" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;$\theta$" title="$\theta$" /></a> values. Given a point <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;$(\xi_0,y_0)$" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;$(\xi_0,y_0)$" title="$(\xi_0,y_0)$" /></a>, and the derivative at that point, <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\begin{align*}&space;z_0&space;=&space;\frac{dy}{d\xi}\Big|_{\xi_0}&space;\end{align*}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\begin{align*}&space;z_0&space;=&space;\frac{dy}{d\xi}\Big|_{\xi_0}&space;\end{align*}" title="\begin{align*} z_0 = \frac{dy}{d\xi}\Big|_{\xi_0} \end{align*}" /></a>, we can write the following equation of a line:

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\begin{align*}&space;y(\xi)-y_0&space;=&space;z_0(\xi-\xi_0)&space;\end{align*}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\begin{align*}&space;y(\xi)-y_0&space;=&space;z_0(\xi-\xi_0)&space;\end{align*}" title="\begin{align*} y(\xi)-y_0 = z_0(\xi-\xi_0) \end{align*}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;$\xi_1$" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;$\xi_1$" title="$\xi_1$" /></a> is defined to be our estimated stellar radius when y becomes zero. Thus:

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\begin{align*}&space;\xi&space;=&space;-\frac{y_0}{z_0}&plus;\xi_0&space;\end{align*}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\begin{align*}&space;\xi&space;=&space;-\frac{y_0}{z_0}&plus;\xi_0&space;\end{align*}" title="\begin{align*} \xi = -\frac{y_0}{z_0}+\xi_0 \end{align*}" /></a>

However, we must make sure that our stepsize <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;$\Delta\xi$" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;$\Delta\xi$" title="$\Delta\xi$" /></a> is small enough that we do not go beyond this estimate.
