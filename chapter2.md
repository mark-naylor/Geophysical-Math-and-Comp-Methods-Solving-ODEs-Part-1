---
title       : Numerical solution to Coupled ODEs
description : Insert the chapter description here



---
## Solving coupled ODEs

```yaml
type: VideoExercise
key: 1bb3ce5d30
lang: python
xp: 50
skills: 2
video_link: player.vimeo.com/video/154783078
```


---
## Solving a coupled ODE

```yaml
type: NormalExercise
key: a5d18d55cf
lang: python
xp: 100
skills: 2
```
 An example is the coupled problem:
  
  $$\frac{dy}{dt}=-x$$
  
  $$\frac{dx}{dt}=y$$

with initial conditions $x(t=0)=1 \mbox{ and } y(t=0)=0$.  

This can be re-written within a vector form, 

Let $z_1 = x$ and $z_2=y$

and $\mathbf{z} =  \begin{pmatrix}z_1 \\ z_2  \end{pmatrix}$

Therefore:
  $$\mathbf{\dot{z}} =  \begin{pmatrix}\dot{z_1} \\ \dot{z_2}  \end{pmatrix} =  \begin{pmatrix}z_2 \\ -z_1 \end{pmatrix}$$

<div class="alert alert-block alert-info"> **IMPORTANT:** Convince yourself that this vector equation for $\mathbf{z}$ is equivalent to the 2 coupled equations for $x,y$ and $t$ above.
</div>

`@instructions`

`@hint`

`@pre_exercise_code`
```{python}
import scipy.interate as integrate
import numpy as np
import matplotlib.pyplot as plt
```

`@sample_code`
```{python}
### Python code to solve coupled pair of ODEs:
###  dy/dt=-x &  dx/dt=y; with initial conditions x=1 y=0

# 1. Define the function f(y,t) that describes the derivative
def derivative(z,t):
  """ Derivative (dz[0]/dt,dz[1]/dt)=(z[1],-z[0])"""
  return (z[1],-z[0])

# 2. Set the evaluation timesteps and initial condition
time=np.linspace(0,10)
y0 = np.array([1,0])

# 3. Use odeint to solve the problem
z = integrate.odeint(derivative, y0, time) 

# 4. Plot the results
plt.plot(time, z[:,0],'k' , linewidth=4)
plt.plot(time,z[:,1],'-gd', linewidth=4)
plt.legend(('Position','Velocity'))
plt.title(r'Solution of $\frac{dy}{dt}=-1, \frac{dx}{dt}=y$' "\n"
    r' $x(0)=1, y(0)=0$'"\n"), plt.xlabel('Time')
```

`@solution`
```{python}
### Python code to solve coupled pair of ODEs:
###  dy/dt=-x &  dx/dt=y; with initial conditions x=1 y=0

# 1. Define the function f(y,t) that describes the derivative
def derivative(z,t):
  """ Derivative (dz[0]/dt,dz[1]/dt)=(z[1],-z[0])"""
  return (z[1],-z[0])

# 2. Set the evaluation timesteps and initial condition
time=np.linspace(0,10)
y0 = np.array([1,0])

# 3. Use odeint to solve the problem
z = integrate.odeint(derivative, y0, time) 

# 4. Plot the results
plt.plot(time, z[:,0],'k' , linewidth=4)
plt.plot(time,z[:,1],'-gd', linewidth=4)
plt.legend(('Position','Velocity'))
plt.title(r'Solution of $\frac{dy}{dt}=-1, \frac{dx}{dt}=y$' "\n"
    r' $x(0)=1, y(0)=0$'"\n"), plt.xlabel('Time')
```

`@sct`
```{python}
test_object("z")
```



---
## Predator Prey Model

```yaml
type: NormalExercise
key: b33db75f69
lang: python
xp: 100
skills: 2
```
We will have a look at the Lotka-Volterra model, also known as the predator-prey equations, which is a pair of first order, non-linear, differential equations frequently used to describe the dynamics of biological systems in which two species interact, one a predator and the other its prey. The model was proposed independently by Alfred J. Lotka in 1925 and Vito Volterra in 1926, and can be described by.

$$\frac{du}{dt} = a \times u - b \times u \times v$$
$$\frac{dv}{dt} = -c \times v + d \times b \times u \times v$$

Where, 

- $u$: number of preys (for example, rabbits)
- $v$: number of predators (for example, foxes)
- $a, b, c, d$ are constant parameters defining the behavior of the population:
    - $a = 1.$ is the natural growing rate of rabbits, when there's no fox
    - $b = 0.1$ is the natural dying rate of rabbits, due to predation
    - $c = 1.5$ is the natural dying rate of fox, when there's no rabbit
    - $d = 0.75$ is the factor describing how many caught rabbits let create a new fox
    
To specify these coupled equations lets use `X=[u,v]`. This is what we want to find by integrating forwards from some known starting population - i.e. the population fo foxes and hares with time.

`@instructions`

- First you need to create a function to return the derivative of `X`below, which we know analytically. 
- Now specify the timerange you want to integrate over and the initial conditions
- Now integrate forward from this initial starting point using `odeint`


`@hint`

`@pre_exercise_code`
```{python}

```

`@sample_code`
```{python}

a = 1.
b = 0.1
c = 1.5
d = 0.75

def dX_dt(X, t=0):
    """ Return the growth rate of fox and rabbit populations. """
    du_dt = a*X[0] -   b*X[0]*X[1]
    dv_dt = -c*X[1] + d*b*X[0]*X[1]
    return np.array([ du_dt ,dv_dt ])
    
t = np.linspace(0, 15,  1000)              # time
X0 = np.array([10, 5])     

## ANSWER
X, infodict = integrate.odeint(dX_dt, X0, t, full_output=True)
infodict['message']                     # >>> 'Integration successful.'

rabbits, foxes = X.T

plt.plot(t, rabbits, 'r-', label='Rabbits')
plt.plot(t, foxes  , 'b-', label='Foxes')
plt.grid()
plt.legend(loc='best')
plt.xlabel('time')
plt.ylabel('population')
plt.title('Evolution of fox and rabbit populations')                 )

```

`@solution`
```{python}
# Definition of parameters
a = 1.
b = 0.1
c = 1.5
d = 0.75

def dX_dt(X, t=0):
    """ Return the growth rate of fox and rabbit populations. """
    du_dt = a*X[0] -   b*X[0]*X[1]
    dv_dt = -c*X[1] + d*b*X[0]*X[1]
    return np.array([ du_dt ,dv_dt ])
    
t = np.linspace(0, 15,  1000)              # time
X0 = np.array([10, 5])     

## ANSWER
X, infodict = integrate.odeint(dX_dt, X0, t, full_output=True)
infodict['message']                     # >>> 'Integration successful.'

rabbits, foxes = X.T

plt.subplot(1,2,1)
plt.plot(t, rabbits, 'r-', label='Rabbits')
plt.plot(t, foxes  , 'b-', label='Foxes')
plt.grid()
plt.legend(loc='best')
plt.xlabel('time')
plt.ylabel('population')
plt.title('Evolution of fox and rabbit populations')

plt.subplot(1,2,1)
plt.plot(foxes, rabbits, 'r-', label='Rabbits')
plt.xlabel("Foxes")
plt.ylabel("Rabbits")
```

`@sct`
```{python}

```




---
## Solving higher order ODEs

```yaml
type: VideoExercise
key: ccb11d82f3
lang: python
xp: 50
skills: 2
video_link: player.vimeo.com/video/154783078
```

`@projector_key`
ded5364ad06fa7eb5f710b0f85081a93

---
## Numercial solution to higher order ODEs

```yaml
type: NormalExercise
key: 299cfd88ab
lang: python
xp: 100
skills: 2
```


`@instructions`

Before we start with a new example, consider the coupled problem we solved above:

  $$\frac{dy}{dt}=-x$$
  
  $$\frac{dx}{dt}=y$$

Substitute the second equation in the first to eliminate $y$:
 $$\frac{dy}{dt}= \frac{d^2x}{dt^2} =-x$$
 
 Similarly, if we eliminate $x$:
 $$\frac{d^2y}{dt^2} =-y$$
 
So in actual fact, these coupled equations can equivalently expressed as 2nd order ODEs!
 
In this Section, we go the other way where we start with a higher order ODE, reformulate as a set of coupled ODEs and then solve with `odeint`.

### Solve the second order ODE:

$$\ddot{y} +2\dot{y} +2y = \cos(2x)$$

with boundary conditions $y \, (x=0)=0$ and $\dot{y} \, (x=0)=0$

- We can turn this into two coupled first-order equations by defining a new dependent variable:

Let
$$z = \frac{dy}{dx} = \dot{y}$$ 
therefore 
$$\dot{z} +2z +2y = \cos(2x)$$

$$\dot{z} = \cos(2x)- 2z - 2y$$

<div class="alert alert-block alert-info"> **IMPORTANT:** Convince yourself that this vector equation for $\mathbf{U}$ is equivalent to the 2 coupled equations for $z,y$ and $t$ above.
</div>

Let 
$$\mathbf{U} = \begin{pmatrix} y \\ z \end{pmatrix}$$

Therefore, the derivative is:
  $$\mathbf{\dot{U}} =  \begin{pmatrix}\dot{y} \\ \dot{z}  \end{pmatrix} =  \begin{pmatrix}z \\ \cos(2x)- 2z - 2y \end{pmatrix} =  \begin{pmatrix} U[1] \\ \cos(2x)- 2 U[0] - 2 U[1] \end{pmatrix}$$


with the two initial boundary conditions $$y\, (x=0)=0$$ and $$\dot{y}\, (x=0)=z\, (x=0)=0$$ 

So, we now have a set of coupled ODEs and if we can integrate $\mathbf{\dot{U}}$ over $x$, we will find $\mathbf{U}$ as a function of position, $x$, which gives us $U[0]=y(x)$ and $U[1]=z=\dot{y}(x)$

<div class="alert alert-block alert-info"> **IMPORTANT:** Convince yourself that this vector equation for $\mathbf{U}$ is equivalent to the 2 coupled equations for $z,y$ and $t$ above.
</div>

`@hint`

`@pre_exercise_code`
```{python}

```

`@sample_code`
```{python}
def dU_dx(U, x):
    # Here U is a vector such that y=U[0] and z=U[1]. This function should return [y', z']
    return [___, ___]

U0 = [___, ___]

x = np.linspace(___, ___, ___)
U = integrate.odeint(___, ___, ___)

# Extract results for plotting
y = U[:,0]
dy_dt = U[:,1]

plt.plot(x,y, label="Position, y")
plt.plot(x, np.cos(2*x), label="Forcing, cos(2x)")
plt.plot(x,dy_dt, label="Velocity, dy/dt")
plt.xlabel("x")
plt.ylabel("y")
plt.title("Damped forced harmonic oscillator");
plt.legend()
```

`@solution`
```{python}
def dU_dx(U, x):
    # Here U is a vector such that y=U[0] and z=U[1]. This function should return [y', z']
    return [U[1], -2*U[1] - 2*U[0] + np.cos(2*x)]

U0 = [0, 0]

x = np.linspace(0, 10, 200)
U = integrate.odeint(dU_dx, U0, x)

# Extract results for plotting
y = U[:,0]
dy_dt = U[:,1]

plt.plot(x,y, label="Position, y")
plt.plot(x, np.cos(2*x), label="Forcing, cos(2x)")
plt.plot(x,dy_dt, label="Velocity, dy/dt")
plt.xlabel("x")
plt.ylabel("y")
plt.title("Damped forced harmonic oscillator");
plt.legend()
```

`@sct`
```{python}

```
