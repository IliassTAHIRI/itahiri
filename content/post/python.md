---
title: "Python Py"
date: 2018-08-02T22:56:18+02:00
subtitle: "The language of the future"
tags: []
---

<!--more-->

My first code in this blog.

The formula : \

$$
a=\frac{1}{\pi}*\int_{I}{b}{x dx}
$$


```python
    import numpy
    import matplotlib as m
    import math as m
    from math import *

    a=10
    b=90
    for i in range(1,5):
      print(i) # print function
```



```python
import matplotlib.pyplot as plt
from matplotlib import rc
import numpy as np
from ipywidgets.widgets import interact, Layout

rc('font', **{'family': 'serif', 'serif': ['Computer Modern'], 'size': 16})
rc('text', usetex=True)
```


```python
Emax = 5
xmin = -2
Lmax = 5
def psi(n, x, L):
    return np.sqrt(2/L) * np.sin(n * np.pi * x / L)
def plt_psi(L):
    x = np.linspace(0,L,100)
    nmax = int(np.sqrt(Emax)*L)
    for n in range(1,nmax+1):
        plt.plot(x, psi(n,x,L)+(n/L)**2, c='r', lw=2, alpha=0.7)
        plt.axhline((n/L)**2, 0, L, c='k')
    plt.ylim(0,6)
    plt.xlim(xmin,Lmax+1)
    plt.axvspan(L, Lmax+1, fc='gray')
    plt.axvspan(-Lmax, 0, fc='gray')
    plt.xlabel(r'$x$')
    plt.ylabel(r'$E \;/(h^2/8m)$')
    plt.show()
```


```python
interact(plt_psi, L=(1, Lmax, 0.1))
```


![png](/img/a_2_0.png)
