---
title: Introduction to numerical solutions to ODEs
description: >-
  In tis chapter, you will explore the basic tools in Python for solving odes.


---
## Classification of Differential Equations

```yaml
type: PureMultipleChoiceExercise
key: 777148f638
xp: 50
skills: 2
```

Which of the below are 1st order ODEs?

1. $\frac{dy}{dx}=4 x^2$
2. $\frac{dy}{dx} - y =4 x^2$
3. $\frac{dy}{dx}= -y \sqrt{x}$
4. $\frac{d^2y}{dx^2}=4 x^2 (1- 3 y)$

`@possible_answers`

- Equation 1
- Equations 1 and 2
- Equations 1 and 3
- [Equations 1, 2 and 3]
- All of them

`@hint`

`@feedbacks`


- There are more
- There are more
- There are more
- Yes - equations 1, 2 and 3 are all first order ODEs
- Equation 4 is a second order ODE

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
- Specify the initial value for $ y_0 = 0.1 $ using `y_initial`

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
times  = np.linspace(___,___,___)  # Time range to integrate over
y_initial = ___                      # Initial value (the starting point for the integration)

# 3. Perform the integration
y=integrate.odeint(func,y_initial,times)

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
y_initial = 0.1                    # Initial value (the starting point for the integration)

# 3. Perform the integration
y=integrate.odeint(func, y_initial, times)

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
test_object("y_initial")
test_object("y")
```


---
## Solving an other ODE using odeint

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: aa63a7a041
```

Use `odeint` to solve,

$\frac{dy}{dt}= -y\sqrt(t)$ with $y(0)=1$ for $t\in(0,5)$

`@instructions`
- Using the alias `integrate` import the package `script.integrate`.
- Import `numpy` and the `matplotlib` plotting package using their standard aliases
- Define the function you wish to integrate and call it `dy_dt`
- Divide the time range into 100 points using `linspace`
- Specify the initial value for $y_0 =1$ using `y0`

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
import matplotlib.___ as ___ # plotting module
import numpy as ___ # numpy module


def dy_dt(___, ___):
    return ___

times = np.linspace(___,___,___)
y0 = ___
y = ___.___(___, ___, ___)

plt.plot(times, y)
plt.xlabel("time")
plt.ylabel("y")

plt.show()

```
`@solution`
```{python}
import scipy.integrate as integrate # get the ODE module
import matplotlib.pyplot as plt # plotting module
import numpy as np # numpy module


def dy_dt(y, t):
    return - y * np.sqrt(t)

times = np.linspace(0,5,100)
y0 = 1.0
y = integrate.odeint(dy_dt, y0, times)

plt.plot(times, y)
plt.xlabel("time")
plt.ylabel("y")

plt.show()

```
`@sct`
```{python}
test_import("scipy.integrate")
test_import("matplotlib.pyplot")
test_import("numpy")
test_object("times")
test_object("y0")
test_object("y")
```

---
## Solving a third ODE using odeint

```yaml
type: NormalExercise
lang: python
xp: 100
skills: 2
key: '8032508806'
```

Use `odeint` to solve,
$$\frac{dy}{dx}+y=x$$

with the initial value of $y(x=0)=1$ over the range $x=0$ to 5 divided into 100 integration points.

`@instructions`
Use what you have learnt in the previous exercises to integrate this derivative

`@hint`
You can rearrange the equation you want to integrate to:

$$\frac{dy}{dx}=x-y$$

The function you define just needs to return the right hand side of this equation



`@sample_code`
```{python}
import ___ as ___ # get the ODE module
import ___ as ___ # plotting module
import ___ as ___ # numpy module

def ___ :
    return ___

x = ___
y0 = ___
y = ___

plt.plot(x, y)
plt.xlabel("x")
plt.ylabel("y")

plt.show()

```
`@solution`
```{python}
import scipy.integrate as integrate # get the ODE module
import matplotlib.pyplot as plt # plotting module
import numpy as np # numpy module

def dy_dx(y, x):
    return x - y

x = np.linspace(0,5,100)
y0 = 1.0
y = integrate.odeint(dy_dx, y0, x)

plt.plot(x, y)
plt.xlabel("x")
plt.ylabel("y")

plt.show()

```
`@sct`
```{python}
test_object("x")
test_object("y0")
test_object("y")
```


