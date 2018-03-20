---
title: Introduction to solving ODEs in Python
key: a951026bf01573a11af7f9dbc6cfc369


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
## Why consider numerical solutions to ODEs

```yaml
type: FullSlide
key: 1fe832c29c
```

`@part1`

Many problems in Geosciences can be written in the form of
differential equations. 

This session aims to introduce you to basic ideas about numerically
solving Ordinary Differential Equations (ODEs) and implementing these in Python.


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

`@script`

---
## Let's practice!

```yaml
type: FinalSlide
key: 036d5e5d8a
```

`@script`

Now it's your turn.

