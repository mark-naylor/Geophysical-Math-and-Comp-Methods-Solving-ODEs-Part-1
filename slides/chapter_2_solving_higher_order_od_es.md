---
title: Solving higher order ODEs
key: ded5364ad06fa7eb5f710b0f85081a93


---
## Solving higher order ODEs

```yaml
type: TitleSlide
key: 72cef53ea8
```

`@lower_third`
name: Mark Naylor
title: Senior Lecturer

`@script`

In this video we will explore how we can use the method we have just developed to solve coupled 1st order ODEs to second and third order ODEs.

---
## Boundary Conditions for Higher Order ODEs

```yaml
type: TwoRows
key: f2eb832c17
```

`@part1`
### Initial Value Problems

- Where all the boundary conditions are specified at the same time or loaction
- If we can construct coupled equations to describe the higher order ODE, we can just start at the known location and integrate away from that point
- This can be done directly using `odeint`

`@part2`
### Boundary Value Problems

- Where the boundary conditions are specified at different times or loactions
- These problems are harder to solve as we need to match BCs at different points
- A classic example is the trajectory of a projectile where the first boundary condition is where it is launched from, and the second is where we want it to land. The problem is to determine the launch angle that will achieve this

`@script`

For a first order ODE we only needed one BC, and we integrated away from that point.

To solve a high order ODEs we need as many BCs as the order of the ODE. So if we have a 2nd order ODE, we need two BCs. Third order, three ...

There is also another consideration that defines the type of problem we will be solving - that is where the boundary conditions are specified.

If all of the BCs are specified at the same time or location, depending upon the problem, we will be able to start at that point in space or time and numerically integrate away from it. These are called initial value problems and are what we will consider in the rest of this Chapter. 

Boundary Value problems are where the BCs are specified at different locations or times and are less trivial to solve. We will consider this type of problem next week.

---
## Higher order ODEs can be expressed as coupled equations

```yaml
type: FullSlide
key: 16d7acc61e
```

`@part1`
Before we start with a new example, consider the coupled problem we solved previously:

  $$\frac{dy}{dt}=-x$$
  
  $$\frac{dx}{dt}=y$$

`@script`

---
## Higher order ODEs can be expressed as coupled equations

```yaml
type: FullSlide
key: 4342113c5d
```

`@part1`
Before we start with a new example, consider the coupled problem we solved above:

  $$\frac{dy}{dt}=-x$$
  
  $$\frac{dx}{dt}=y$$

Substitute the second equation in the first to eliminate $y$:
 $$\frac{dy}{dt}= \frac{d^2x}{dt^2} =-x$$

`@script`

If we subsititute the second equation into the first, we can eliminate y and end up with a second order ODE in x and t.


---
## Higher order ODEs can be expressed as coupled equations

```yaml
type: FullSlide
key: 6a73e66804
```

`@part1`
Before we start with a new example, consider the coupled problem we solved above:

  $$\frac{dy}{dt}=-x$$
  
  $$\frac{dx}{dt}=y$$


Substitute the second equation in the first to eliminate $y$:
 $$\frac{dy}{dt}= \frac{d^2x}{dt^2} =-x$$


 Similarly, if we eliminate $x$:
 $$\frac{d^2y}{dt^2} =-y$$
 
`@script`

Similarly, if we subsititute the first equation into the second, we can eliminate x and end up with a second order ODE in y and t.

So in actual fact, these coupled equations are equivalently expressed as 2nd order ODEs!

The methods we will be exploring will take a 2nd order ODE, convert it to a set of coupled ODEs and then solving these using odeint.

---
## EXAMPLE: Damped Simple Harmonic Oscillator

```yaml
type: FullSlide
key: fd47dc0589
```

`@part1`

Solve the second order ODE:

$$\ddot{y} +2\dot{y} +2y = \cos(2t)$$

with the initial condition $y=0$ and $\dot{y}=0$ at $t=0$.

`@script`

The damped SHO is a standard system, commonly used in physics.

In the exercises later, you will use this model to model the response of a seismometer.

If we can reformulate the problem as a set of coupled 1st order ODEs, we can use what we have learned in previous exercises so solve this problem!

---
## EXAMPLE: Damped Simple Harmonic Oscillator (Part 1)

```yaml
type: FullSlide
key: '3273522130'
```

`@part1`

- Solve the second order ODE:

$$ \ddot{y} +2 \dot{y} +2y = \cos(2t) $$

with the initial condition $y=0$ and $\dot{y}=0$ at $t=0$.

- Lets start by defining a new vector $ U = ( z0 , z1 ) $ where $z0 =y$ and $z1 =\dot{y}$ 

- Next take its derivative,
  $$\dot{U} =  (\dot{z0} , \dot{z1} )$$

`@script`

---
## EXAMPLE: Damped Simple Harmonic Oscillator (Part 2)

```yaml
type: FullSlide
key: 4304b431b0
```

`@part1`
 Now consider the two terms in the bracket on the RHS of $\dot{U} =  (\dot{z0} , \dot{z1} )$,

- Since $z0 = y$, 
 $$ \dot{ z0 } = \dot{ y } = z1 $$
 
- and since $z1=\dot{y}$,
 $$ \dot{ z1 } = \ddot{y} = \cos (2t) - 2 \dot{y} - 2y= \cos (2t) - 2 z1 - 2 z0$$

`@script`

---
## EXAMPLE: Damped Simple Harmonic Oscillator (Part 2)

```yaml
type: FullSlide
key: '20537484e2'
```

`@part1`
Now consider the two terms in the bracket on the RHS of $\dot{U} =  (\dot{z0} , \dot{z1} )$,

- Since $z0 = y$, 
 $$ \dot{ z0 } = \dot{ y } = z1 $$
 
- and since $z1=\dot{y}$,
 $$ \dot{ z1 } = \ddot{y} = \cos (2t) - 2 \dot{y} - 2y= \cos (2t) - 2 z1 - 2 z0$$

- If you look carefully, we now have two coupled 1st order equations:
$$ \dot{ z0 } = z1 $$
$$ \dot{ z1 } = \cos (2t) - 2 z1 - 2 z0$$

`@script`

---
## Defining the function for the coupled derivatives

```yaml
type: TwoRows
key: 5c5f49251c
```

`@part1`

- Coupled ODE example: $dy/dt=-x$ and  $dx/dt=y$
```
def derivative(z,t):
  """ Derivative (dz[0]/dt,dz[1]/dt)=(z[1],\cos (2t) - 2 z1 - 2 z0)"""
  return ( z[1], -z[0] )
```

`@part2`
- 2nd order Simple Harmonic Oscillator
$$ \dot{ z }[0] = z[1] $$
$$ \dot{ z }[1] = \cos (2t) - 2 z[1] - 2 z[0]$$

```
def dU_dt(z,t):
  """ Derivative (dz[0]/dt,dz[1]/dt)=(z[1],\cos (2t) - 2 z[1] - 2 z[0])"""
  return ( z[1], np.cos(2*t)-2*z[1]-2*z[0] )
```

`@script`

---
## Let's practice!

```yaml
type: FinalSlide
key: 9ed213dd20
```

`@script`

Now let's try some examples.

