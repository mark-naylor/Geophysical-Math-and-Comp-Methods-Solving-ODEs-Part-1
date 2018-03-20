---
title       : Numerical solution to Coupled ODEs
description : Insert the chapter description here


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
