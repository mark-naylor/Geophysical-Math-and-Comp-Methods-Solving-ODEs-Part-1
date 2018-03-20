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




---
## Higher order ODEs can be expressed as coupled equations

```yaml
type: FullSlide
key: 16d7acc61e
```

`@part1`
Before we start with a new example, consider the coupled problem we solved above:

  $$\frac{dy}{dt}=-x$$
  
  $$\frac{dx}{dt}=y$$

`@part2`
Substitute the second equation in the first to eliminate $y$:
 $$\frac{dy}{dt}= \frac{d^2x}{dt^2} =-x$$

`@part3` 
 Similarly, if we eliminate $x$:
 $$\frac{d^2y}{dt^2} =-y$$
 
`@part4`
So in actual fact, these coupled equations can equivalently expressed as 2nd order ODEs!
 
`@part5`
In this Section, we go the other way where we start with a higher order ODE, reformulate as a set of coupled ODEs and then solve with `odeint`.

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
 

So in actual fact, these coupled equations can equivalently expressed as 2nd order ODEs!
 
`@script`


---
## EXAMPLE: Damped Simple Harmonic Oscillator

```yaml
type: FullSlide
key: 805e454a12
```

`@part1`

Solve the second order ODE:

$$\ddot{y} +2\dot{y} +2y = \cos(2x)$$

with boundary conditions $y \, (x=0)=0$ and $\dot{y} \, (x=0)=0$

`@script`

---
## EXAMPLE: Damped Simple Harmonic Oscillator

```yaml
type: FullSlide
key: fd47dc0589
```

`@part1`

Solve the second order ODE:

$$\ddot{y} +2\dot{y} +2y = \cos(2x)$$

with the initial condition $y=0$ and $\dot{y}=0$ at $x=0$.

`@script`

---
## EXAMPLE: Damped Simple Harmonic Oscillator (Part 1_

```yaml
type: FullSlide
key: '3273522130'
```

`@part1`

- Solve the second order ODE:

$$ \ddot{y} +2 \dot{y} +2y = \cos(2x) $$

with the initial condition $y=0$ and $\dot{y}=0$ at $x=0$.

- To solve this we define a new vector 

$ U = ( z_{1} , z_{2} ) $

where $z_{1} =u$ and $z_{2} =\dot{y}$ 

- And take its derivative:
  $$\dot{U} =  (\dot{z_{1}} , \dot{z_{2}} )$$


`@script`

---
## EXAMPLE: Damped Simple Harmonic Oscillator (Part 2

```yaml
type: FullSlide
key: 4304b431b0
```

`@part1`

$$\dot{U} =  (\dot{z_{1}} , \dot{z_{2}} )$$
  
 Let's consider the two terms in the bracket on the RHS of this equation,
 
 $$ \dot{ z_{1} } = \dot{ y } = z_{2} $$
 
 and
 
 $$ \dot{ z_{2} } = \ddot{y} = \cos (2x) - 2 \dot{y} - 2y= \cos (2x) - 2 z_{2} - 2 z_{1}$$

- We can also need to express the intial conditions in terms of $z_{1}$ and $z_{2}$.

$$y(x=0)=z_{1}(x=0)=0$$

$$\dot{y}(x=0)=z_{2}(x=0)=0$$


`@script`


---
## EXAMPLE: Damped Simple Harmonic Oscillator (Part32

```yaml
type: FullSlide
key: 26ac696de8
```

`@part1`

- So, we now have a set of coupled ODEs and if we can integrate $\dot{U}$ over $x$, we will find $U$ as a function of position, $x$, which gives us $U[0]=y(x)$ and $U[1]=z=\dot{y}(x)$

 **IMPORTANT:** Convince yourself that this vector equation for $U$ is equivalent to the 2 coupled equations for $z,y$ and $t$ above.
`@script`

---
## Let's practice!

```yaml
type: FinalSlide
key: 9ed213dd20
```

`@script`

Now let's try some examples.

