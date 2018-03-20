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
name: Firstname Lastname
title: Instructor

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
## Example- Damped Simple Harmonic Oscillator

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
## Let's practice!

```yaml
type: FinalSlide
key: 9ed213dd20
```

`@script`

Now let's try some examples.

