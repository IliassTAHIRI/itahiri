---
title: "Python : The language of the future "
subtitle: The language of the future
date: 2018-08-02T22:56:18+02:00
tags: []
---

<!--more-->


# Cohesive Mohr-Coulomb interface effects on the strength criterion of materials with granular-based microstructure


```python
from numpy import *
from numpy.linalg import *
import matplotlib.pyplot as plt
import matplotlib as mlp
import numpy as np
from scipy.stats import uniform
import seaborn as sns
from sympy import *
```

## Homogenized elastic parameters

$C_{hom}=3k_{hom}JI+2\mu_{hom}IK$

$\mu_{hom}=K_{n}r_0M(k,\phi)$

$k_{hom}=K_{n}r_0K(k,\phi)$

When $\phi_0<1/3$:

$K(\phi_0,\rho)=R_0(\phi_0)+R_1(\phi_0)\rho$

$R_0(\phi_0)=\frac{2}{3}(1-3\phi_0)$ et $R_1(\phi_0)=\frac{8\phi_0(3\phi_0-2)^2}{(3\phi_0-4)(3\phi_0-1)}$


```python
#Calculation of homogenized parameters in the case of p0<0.3333...
p0, rho, Kn, r0, lamda, h, alpha= symbols("p0 rho Kn r0 lambda h alpha")
R0=(2/3)*(1-3*p0)
R1=(8*p0*(3*p0-2)**2)/((3*p0-4)*(3*p0-1))
M0=(1/4)*(1-3*p0)
M1=(3*(1-p0)*(3*p0-2)**2)/(2*(3*p0-4)*(3*p0-1))
R=R0+R1*rho
M=M0+M1*rho
mu_hom=Kn*r0*M
k_hom=Kn*r0*K
#b=
#N=
################## Calculation of k_hom and µ_hom for a given microscopic values
r0_1=0.1 ; Kn_1=1 ; p0_1=0.25 ;rho_1=0.5
k_hom_1 = k_hom.subs(p0, p0_1).subs(Kn,Kn_1).subs(r0,r0_1).subs(rho,rho_1)
k_hom_1 = mu_hom.subs(p0, p0_1).subs(Kn,Kn_1).subs(r0,r0_1).subs(rho,rho_1)
print(r"k_hom=", k_hom_1)
```

    k_hom= 0.114423076923077


## Determination of homogenized strength

Mohr-Coulomn interface and rigid grains

Strength of the grains is assumed to be infinite

The strength properties of an interface characterized by a Mohr-Coulomb failure criterion are defined by a condition on the stress vector T acting on this interface:

$f^I(T)=T_t + \alpha(T_n-h)<=0$



```python

```

## Macroscopic strength criterion

## The case of $\phi<1/3$

## The case of $\phi>=1/3$

Case of $\delta>1$


```python
def Case_delta_sup_1(h_0,p_0,alpha_0):
    lamda=((1-p0)**2)*(1-2*p0)
    KK=(4*(1-p0)*(1-2*p0))/((3*p0)*(3*p0-1))
    MM=(1-2*p0)/(3*p0-1)
    delta=3*(alpha**2)*KK/(2*lamda)
    AA=h*lamda*(delta**0.5)/(delta-1)
    BB=h*lamda*((2*delta*MM)/((delta-1)*KK))**0.5
    C=h*lamda*delta/(delta-1)
    AA1 = AA.subs(h, h_0).subs(p0,p_0).subs(alpha, alpha_0)
    BB1 = BB.subs(h, h_0).subs(p0,p_0).subs(alpha, alpha_0)
    C1 = C.subs(h, h_0).subs(p0,p_0).subs(alpha, alpha_0)


#Case_delta_sup_1(40,0.4,0.2)
```

Case of $\delta<1$


```python
def Case_delta_inf_1(h_0,p_0,alpha_0):
    A=h*lamda*(delta**0.5)/(1-delta)
    B=h*lamda*((2*delta*MM)/((1-delta)*KK))**0.5
    C=h*lamda*delta/(delta-1)

    A1 = A.subs(h, h_0).subs(p0,p_0).subs(alpha, alpha_0)
    B1 = B.subs(h, h_0).subs(p0,p_0).subs(alpha, alpha_0)
    C1 = C.subs(h, h_0).subs(p0,p_0).subs(alpha, alpha_0)
    m = np.linspace(-0.5,0.06,200)
    d = np.linspace(0,0.1,200)


    m,d = np.meshgrid(m,d)
    M = (B1**2) * ((1/(h_i*h_i)) - ((m-(C1/h_i))/A1)**2 )
    D = d**2
    plt.contour(m,d,(M-D),[0])
    plt.xlabel(r'$\frac{\Sigma_m}{h}$')
    plt.ylabel(r'$\frac{\Sigma_d}{h}$')
    plt.legend(loc=4)

#Case_delta_inf_1(40,0.4,0.2)
```

## Weakly frictional interfaces for $\phi_0>1/3$


```python
######################################################################
################## 4.2.1 Weakly frictional interfaces
######################################################################
def Case_delta_inf_1(h_i, p_i, a_i):
    A  = -1*h*alpha*((1-p0)**2)*(1-2*p0)*(2*p0*(3*p0-1)*(1-p0))**0.5  / (2*alpha**2-p0*(3*p0-1)*(1-p0))
    B  = h*alpha*(1-p0)*(1-2*p0)    *   ((3*p0*(-1+p0))/((2*(alpha**2)-p0*(3*p0-1)*(1-p0))))**0.5
    C  = (2*alpha**2*h*((1-p0)**2)*(1-2*p0))/(2*(alpha**2)-p0*(3*p0-1)*(1-p0))
    A1 = A.subs(h, h_i).subs(p0,p0_i).subs(alpha, a_i)
    B1 = B.subs(h, h_i).subs(p0,p0_i).subs(alpha, a_i)
    C1 = C.subs(h, h_i).subs(p0,p0_i).subs(alpha, a_i)
    m = np.linspace(-0.26,0.06,200)
    d = np.linspace(0,0.1,200)


    m,d = np.meshgrid(m,d)
    M = (B1**2) * ((1/(h_i*h_i)) - ((m-(C1/h_i))/A1)**2 )
    D = d**2
    plt.contour(m,d,(M-D),[0])
    plt.xlabel(r'$\frac{\Sigma_m}{h}$')
    plt.ylabel(r'$\frac{\Sigma_d}{h}$')
    plt.legend(loc=4)

h_i=40; p_i= 0.4 ; alpha_i=[0.06,0.09,0.12]
for i in range(len(alpha_i)):
    Case_delta_inf_1(h_i,p_i,alpha_i[i])


```

    No handles with labels found to put in legend.
    No handles with labels found to put in legend.
    No handles with labels found to put in legend.



![png](output_files/output_16_1.png)


## Strongly frictional interfaces for $\phi_0>1/3$


```python
######################################################################
################## 4.2.1 Strongly frictional interfaces
######################################################################
def Case_delta_inf_1(h_0,p_0,a_i):
    AA=h*alpha* ((1-p0)**2)*(1-2*p0)*(2*p0*(3*p0-1)*(1-p0))**0.5  / (2*alpha**2-p0*(3*p0-1)*(1-p0))
    BB=h*alpha*(1-p0)*(1-2*p0)    *   ((3*p0*(1-p0))/((2*(alpha**2)-p0*(3*p0-1)*(1-p0))))**0.5
    C=(2*alpha**2*h*((1-p0)**2)*(1-2*p0))/(2*(alpha**2)-p0*(3*p0-1)*(1-p0))
    A1 = AA.subs(h, h_0).subs(p0,p_0).subs(alpha, a_i)
    B1 = BB.subs(h, h_0).subs(p0,p_0).subs(alpha, a_i)
    C1 = C.subs(h, h_0).subs(p0,p_0).subs(alpha, a_i)
    m = np.linspace(-0.3,0.1,200)
    d = np.linspace(0,1,200)
    m,d = np.meshgrid(m,d)
    M = (B1**2) * (-(1/(h_i*h_i)) + ((m-(C1/h_i))/A1)**2 )
    D = d**2
    plt.contour(m,d,(D-M),[0])
    plt.xlabel(r'$\frac{\Sigma_m}{h}$')
    plt.ylabel(r'$\frac{\Sigma_d}{h}$')
    plt.legend(loc=4)

h_i=40; p_i= 0.4 ; alpha_i=[0.2,0.3,0.5]
for i in range(len(alpha_i)):
    Case_delta_inf_1(h_i,p_i,alpha_i[i])
```

    No handles with labels found to put in legend.
    No handles with labels found to put in legend.
    No handles with labels found to put in legend.



![png](output_files/output_18_1.png)



```python

```
