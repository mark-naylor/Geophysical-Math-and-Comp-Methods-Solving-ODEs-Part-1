---
title: Solving coupled ODEs
key: 580a94edd2ef9105f394e28f32ba16cc


---
## Solving coupled ODEs

```yaml
type: TitleSlide
key: 02ab7a1102
```

`@lower_third`
name: Mark Naylor
title: Senior Lecturer

`@script`





---
## Solving coupled 1st order ODEs with `odeint`

```yaml
type: TwoRows
key: 6f0ba9b200
```

`@part1`
Solve the coupled equations, 

  $$\frac{dy}{dt}=-x \qquad \frac{dx}{dt}=y$$

with initial conditions $x(t=0)=1$ and $y(t=0)=0$.  

`@part2`
```
def dz_dt(z,t):                         # 1. Derivative function
  return (z[1],-z[0])

z0 = np.array([1,0])                    # 2. Initial conditions

time = np.linspace(0,10)                # 3. Define domain

z = integrate.odeint(dz_dt, z0, time)   # 4. Integrate
```

`@script`

Basically, we want to know how x and y vary in time. We know the values of x and y at t=0. We want to integrtate the coupled odes forward in time to find the values upto and including t=10.

- Easy to do for initial value problems
- Return all the derivatives from the function we define
- Specify all the initial conditions in a single array


---
## EXAMPLE: Lotka-Volterra model - Predator-Prey

```yaml
type: FullSlide
key: 2d7f40fb2f
```

`@part1`
These are pair of 1st order, non-linear, ODEs frequently used to describe the dynamics of biological systems in which two species interact, one a predator and the other its prey. 

The model was proposed independently by Alfred J. Lotka in 1925 and Vito Volterra in 1926, and can be described by.

$$\frac{du}{dt} = a \times u - b \times u \times v$$
$$\frac{dv}{dt} = -c \times v + d \times b \times u \times v$$

Where, 

- $u$: number of preys (for example, rabbits)
- $v$: number of predators (for example, foxes)

`@script`
The interaction of predator-prey demonstrates how coupled ODEs behave.

A classic example is the competition between the snowshoe hare and arctic fox populations.
---
## EXAMPLE: Lotka-Volterra model - Predator-Prey

```yaml
type: FullSlide
key: 8ba60f91eb
```

`@part1`
$$\frac{du}{dt} = a \times u - b \times u \times v \qquad \frac{dv}{dt} = -c \times v + d \times b \times u \times v$$

- $u$: number of preys (for example, rabbits)
- $v$: number of predators (for example, foxes)
- $a, b, c, d$ are constant parameters defining the behavior of the population:
    - $a = 1.$ is the natural growing rate of rabbits, when there's no fox
    - $b = 0.1$ is the natural dying rate of rabbits, due to predation
    - $c = 1.5$ is the natural dying rate of fox, when there's no rabbit
    - $d = 0.75$ is the factor describing how many caught rabbits let create a new fox


`@script`


---
## Let's practice!

```yaml
type: FinalSlide
key: 2cbfa777eb
```

`@script`

Now let's try some examples.

