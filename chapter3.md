---
title       : Under the lid - How do numerical ODE solvers work?
description : This chapter introduces you to the basics of how numerical ODE solvers work. We will explore how the Euler and Implicit methods work and look to how these can be refined to give better accuracy.
---
## Euler's Method to solve a first order ODE

```yaml
type: NormalExercise
key: 2162b470b9
lang: python
xp: 100
skills: 2
```

Solving a $1^{st}$ Order ODE using Euler's Method where the derivative is equal to some arbitary function $f$.

$ \frac{dy}{dx}=f(y,x) $ 

At some node, $n$

$ \frac{ y_{n+1} - y_{n} }{h} \approx f_{n} $ 

Which we can rearrange to find the next value $y_{n+1}$ based on the current value $y_{n}$ and the value of the function at the current position $f_{n}$.




`@instructions`
- Solve $dy/dt=t$

$ y_{n+1} = y_{n} + f_{n} . h $

Becomes,

$ y_{n+1} = y_{n} + t . h $

- Over the domain $y \in(0,2)$ 

- Using the initial condition $y(t=0)=0$ so `y[0]=0`

`@hint`

`@pre_exercise_code`
```{python}

```

`@sample_code`
```{python}
#############################################################
# Compute y iteratively using Finite Difference Forward Euler

import numpy as np
import matplotlib.pyplot as plt

h=0.1 # Stepsize

# Create output arrays
t = np.arange(0,2,h)    # Array of output times from 0 to 2 in 0.1 increments
y = np.empty_like(t)    # An empty array to store the y in

N = len(t)              # The length of t tells us how many interations are needed

y[0] = 0                # Set the first value in y to be the initial condition y(t=0)=0

# Numerially iterate over time using the forward Euler discretisation
for n in range(0,N-1):
    y[n+1] = y[n] + h * t[n]

plt.plot(t, y, "--+", label="Euler's Solution")
plt.xlabel("Time")         ;       plt.ylabel("y")
plt.legend(loc="upper left")



```

`@solution`
```{python}
#############################################################
# Compute y iteratively using Finite Difference Forward Euler

import numpy as np
import matplotlib.pyplot as plt

h=0.1 # Stepsize

# Create output arrays
t = np.arange(0,2,h)    # Array of output times from 0 to 2 in 0.1 increments
y = np.empty_like(t)    # An empty array to store the y in

N = len(t)              # The length of t tells us how many interations are needed

y[0] = 0                # Set the first value in y to be the initial condition y(t=0)=0

# Numerially iterate over time using the forward Euler discretisation
for n in range(0,N-1):
    y[n+1] = y[n] + h * t[n]

plt.plot(t, y, "--+", label="Euler's Solution")
plt.xlabel("Time")         ;       plt.ylabel("y")
plt.legend(loc="upper left")



```

`@sct`
```{python}

```
