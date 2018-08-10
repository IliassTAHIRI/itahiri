---
title: "Python Py"
date: 2018-08-02T22:56:18+02:00
subtitle: "The language of the future"
tags: []
---

<!--more-->

Solving a variety types of problems using Python :

#### Solving mathematical riddles:
Problem : how many multiples of 5 or 7 under 1000.

```python

r=0

for i in range(1000):
    if i % 5 ==0 or i % 7 == 0:
        print(i)
        
        r+=i
        
print(r)

```
The result is 233168.

#### Solving equations:

Many method exists to simple or complex equation in python. The Sympy library is one of many possible ways to solve an equation. Lets solve the equation that follows for x.

$$
x^2+x+1=0
$$

```python

from sympy import *
x = Symbol('x')
solve(x**2-100)
```
The equation have 2 solutions. The results are in a list form.

```python
# Result
Out[]: [-10, 10]

```

#### Plotting data with matplotlib:




