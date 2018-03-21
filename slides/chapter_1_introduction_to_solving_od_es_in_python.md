---
title: Introduction to solving ODEs in Python
key: a951026bf01573a11af7f9dbc6cfc369

video_link: //player.vimeo.com/video/78834424

---
## Introduction to solving ODEs in Python

```yaml
type: TitleSlide
key: 13c8ff64fe
```

`@lower_third`
name: Mark Naylor
title: Instructor

`@script`





---
## Why consider numerical solutions to differential equations?

```yaml
type: FullSlide
key: 1fe832c29c
```

`@part1`

- Many problems in Geosciences can be written in the form of differential equations. 

- Broadly, this is because for things to flow and change, we need gradients to exist in the environment to drive, control and mediate that change. Differential equations are the fundemental vocabulary of such gradients and changes.

- This first chapter, we introduce you to basic ideas about numerically solving the simplest differential equations, 1st order Ordinary Differential Equations (ODEs) and using `scipy.integrate.odeint` in Python.


`@script`

---
## What are Ordinary differential equations?

```yaml
type: FullSlide
key: 5e2281805c
```

`@part1`
- In mathematics, an ordinary differential equation (ODE) is a differential equation containing one or more functions of one independent variable and its derivatives. 
- The term ordinary is used in contrast with the term partial differential equation which may be with respect to more than one independent variable.

`@script`



---
## What information is needed to solve a 1st order ODE?

```yaml
type: TwoRows
key: f2eb832c17
```

`@part1`
We need four elements to solve an ode. The first three below are the same information you need to analytically solve an ODE. 

1. The funtion we want to integrate:

2. Boundary Conditions: 

3. Domain to integrate over:

4. A numerical ODE solver: `scipy.integrate.odeint`



`@script`
Instead of analyitically solving the equation, we need a numerical ODE solver.

---
## Numerical solution of 1st order ODEs using `odeint`

```yaml
type: FullSlide
key: 022f1030d2
```

`@part1`

`scipy.integrate.odeint`

Scipy provides the function `scipy.integrate.odeint` which can
  use a variety of solvers to solve 1st order ODEs.

  `odeint` is run as
  `y=scipy.integrate.odeint(fn,yo,t)` where:

- `fn`: is the function you want to solve corresponding to $dy/dt=$ `fn(y,t)`. 
- `fn`: should be a function of $y$ and $t$ i.e. `fn(y,t)`.
- `t`: specifies the times you want solution values for.
- `y0`: are the initial conditions.
- `args`: You can provide other arguments for `odeint` including additional arguments for the function to be solved. 

`@script`


---
## An example of `odeint`

```yaml
type: FullSlide
key: 979e3f9b42
```

`@part1`

How can we solve $\frac{dy}{dt}=t$ using `odeint`?

``` 
# 1. Define the function you want to integrate
def dy_dt(y,t):
  return (t)

# 2. Boundary condition
yinit = 0.1

# 3. Domain to integrate over
time  = np.linspace(0,10,100)

# 4. Perform the integration
y=integrate.odeint(dy_dt, yinit, time)

# 5. Plot the results
plt.plot(time,y)

plt.xlabel('time')    ;    plt.ylabel('y')
plt.title(r'Solution for $\frac{dy}{dt}=t$')
```

`@script`


---
## Let's practice!

```yaml
type: FinalSlide
key: 036d5e5d8a
```

`@script`

Now it's your turn.

