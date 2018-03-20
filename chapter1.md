---
title: Introduction to numerical solutions to ODEs
description: >-
  In tis chapter, you will explore the basic tools in Python for solving odes.


---
## Sample exercise

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: 988b99648b
```



`@instructions`
Solve $\frac{dy}{dt}=t$ using `odeint`

-

`@hint`



`@sample_code`
```{python}
import scipy.integrate as integrate # get the ODE module
import matplotlib.pyplot as plt # plotting module
import numpy as np # numpy module

# 1. Define the function you want to integrate
def func(y,t):
  """ Simple function to illustrate use of scipy.integrate.ode for the problem dy/dt=t """
  return (t)

# 2. Specify the arguments for the integration
time  = np.linspace(0,10,100)  # Time range to integrate over
yinit = np.array(0.1)          # Initial value (the starting point for the integration)

# 3. Perform the integration
y=integrate.odeint(func,yinit,time)

# 4. Plot the results
plt.plot(time,y)
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
time  = np.linspace(0,10,100)  # Time range to integrate over
yinit = np.array(0.1)          # Initial value (the starting point for the integration)

# 3. Perform the integration
y=integrate.odeint(func,yinit,time)

# 4. Plot the results
plt.plot(time,y)
plt.xlabel('time')    ;    plt.ylabel('y')
plt.title(r'Solution for $\frac{dy}{dt}=t$')

plt.show()
```





