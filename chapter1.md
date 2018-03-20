---
title: Introduction to numerical solutions to ODEs
description: >-
  In tis chapter, you will explore the basic tools in Python for solving odes.


---
## Solving an ODE using odeint

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: 988b99648b
```

In this exercise you will use the `scipy.integrate` module to numerically integrate a 1st order ODE.


Scipy provides the function `scipy.integrate.odeint` which can
  use a variety of solvers to solve 1st order ODEs.

  `odeint` is run as
  `y=scipy.integrate.odeint(fn,yo,t)` where:

- `fn`: is the function you want to solve corresponding to $dy/dt=$ `fn(y,t)`. 
- `fn`: should be a function of $y$ and $t$ i.e. `fn(y,t)`.
- `t`: specifies the times you want solution values for.
- `y0`: are the initial conditions.
- `args`: You can provide other arguments for `odeint` including additional arguments for the function to be solved.

`@instructions`
In these instructions, you will explore the basic elements required to solve an ODE using `odeint`
- Using the alias `integrate` import the package `script.integrate`. From this package you will be able to call odeint`
- First, we need to define the function you want to integrate. This is called `func` in the example code. If you want to integrate $dy/dt$ then the function you define is `func(y,t)`.
- `func` needs to return the derivative. Since we are integrating $dy/dt=t$, we just need to return the right hand side of this equation.
- Next we need to define the range of times we want to integrate over. Use `linspace` to generate a array over the range 0 to 10 broken down into 100 steps.
- Specify the initial value for $y_0 = 0.1$ using `y_initial`

`@hint`
1. Simple function to illustrate use of scipy.integrate.ode for the problem dy/dt=t
``` 
def func(y,t):
  return (t)
```

2. 
```times  = np.linspace(0,10,100)  # Time range to integrate over```

3. 
```y_init = np.array(0.1)          # Initial value (the starting point for the integration)```


`@sample_code`
```{python}
import ___ as ___ # get the ODE module
import matplotlib.pyplot as plt # plotting module
import numpy as np # numpy module

# 1. Define the function you want to integrate
def func(___,___):
  """ Simple function to illustrate use of scipy.integrate.ode for the problem dy/dt=t """
  return (___)

# 2. Specify the arguments for the integration
time  = np.linspace(___,___,___)  # Time range to integrate over
y_init = np.array(___)          # Initial value (the starting point for the integration)

# 3. Perform the integration
y=integrate.odeint(func,y_init,times)

# 4. Plot the results
plt.plot(times,y)
plt.xlabel('time')    ;    plt.ylabel('y')
plt.title(r'Solution for $\frac{dy}{dt}=t$')

plt.show()
```
`@solution`
```{python}
import scipy.integrate as integrate # get the ODE module
import matplotlib.pyplot as plt # plotting module
import numpy as np # numpy module

# 1. Define the function you want to integrate
def func(y,t):
  """ Simple function to illustrate use of scipy.integrate.ode for the problem dy/dt=t """
  return (t)

# 2. Specify the arguments for the integration
times  = np.linspace(0,10,100)  # Time range to integrate over
y_init = np.array(0.1)          # Initial value (the starting point for the integration)

# 3. Perform the integration
y=integrate.odeint(func, y_init, times)

# 4. Plot the results
plt.plot(times,y)
plt.xlabel('time')    ;    plt.ylabel('y')
plt.title(r'Solution for $\frac{dy}{dt}=t$')

plt.show()
```
`@sct`
```{python}
test_import("scipy.integrate")
test_object("times")
test_object("y_init")
test_object("y")
```




