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
type: TwoRowsTwoColumns
key: 6f0ba9b200
```

`@part1`
- Easy to do for initial value problems
- Return all the derivatives from the function we define
- Specify all the initial conditions in a single array

`@part2`

```
# 1. Derivative function
def dz_dt(z,t):
  return (z[1],-z[0])

# 2. Initial conditions
z0 = np.array([1,0])

# 3. Define domain
time=np.linspace(0,10)

# 3. integrate
z = integrate.odeint(dz_dt, z0, time) 
```

`@part3`
  $$\frac{dy}{dt}=-x$$
  
  $$\frac{dx}{dt}=y$$

with initial conditions $x(t=0)=1$ and $y(t=0)=0$.  


`@script`


---
## <<<New Slide>>>

```yaml
type: TwoRowsTwoColumns
key: cb9f37d5ed
```

`@part1`

`@part2`

`@part3`

`@part4`

`@script`

---
## EXAMPLE: Predator-Prey

```yaml
type: TwoColumns
key: 2d7f40fb2f
```

`@part1`
- 
`@part2`

`@script`
The interaction of predator-prey demonstrates how coupled ODEs behave.

A classic example is the competition between the snowshoe hare and arctic fox populations.

---
## Let's practice!

```yaml
type: FinalSlide
key: 2cbfa777eb
```

`@script`

Now let's try some examples.

