---
title: "Python"
subtitle: 
date: 2018-08-02T22:56:18+02:00
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
> The result is 233168.

#### Solving equations:

Many method exists to simple or complex equation in python. The Sympy library is one of many possible ways to solve an equation. Lets solve the equation that follows for x.

$$
x^2-100=0
$$

```python

from sympy import *
x = Symbol('x')
solve(x**2-100)
```
> The equation have 2 solutions. The results are in a list form.

```python
# Result
Out[]: [-10, 10]

```
\
#### Plotting data with matplotlib:

The source of data is the United Nations World Population Prospects :

```python

import matplotlib.pyplot as plt

year=[1950,1955,1960,1965,1970,1975,1980,1985,1990,1995,2000,2005,2010,2015,2016,2017,2018]

population = [8985989,10502666,12328532,14229044,16000008,17803698,20019847,22537376,24879136,27075232,28849621,30521070,32409639,34803322,35276786,35739580,36191805]

plt.xlabel('Year')
plt.ylabel('Population')
plt.title('Evolution of population in Morocco')
plt.plot(year,population)

```


<div class="figure"><span id="fig:pie"></span>
<img src="f.png" alt="" width="672" />
<p class="caption">
Figure 1: Population of Morocco through the years.
</p>
</div>
