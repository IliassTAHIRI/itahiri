---
title: Diffusion properties of coal matrix
subtitle: Numerical analysis of their impact on fluid transfer in coal reservoir
date: 2018-09-11
author: I. TAHIRI


slug: diffusion-properties-of-coal-matrix-numerical-analysis-of-their-impact-on-fluid-transfer-in-coal-reservoirs

categories:
  - Science
  - Research
  - Mathematics
tags: []
---

<!--more-->

<div style="text-align: justify">
Enhanced coalbed methane is a technique used to improve the recovery of methane (CH4) from coalbeds. It consists in the injection of a fluid (CO2 ,N2) in a well and recover CH4 in an other well.

<div class="figure"><span id="fig:pie"></span>
<img src="co2inj.JPG" alt="" width="500" />
<p class="caption">
Figure : Enhaced coalbed methane recovery.
</p>
</div>

However, the injection of CO2 affect the swelling properties of coal due to the adsorption process. The swelling also affect the permeability of coal, that is considered one of the most important parameters in reservoir simulations. The aim is to determine by inverse calculation the permeability of a coal matrix using existing experimental data. The approach consists first in solving the direct problem of flow and swelling of coal matrix using a mixes approach of numerical and analytical resolution. Second, the inverse analysis consists in minimizing the chosen cost function in order to calculate the unknown parameters.

###Direct problem of flow and swelling of coal matrix
To derive the governing equation for flow of gas in the coal matrix, the mass conservation
equation, Darcy’s law and the equation of state of the fluid are combined.
The resulting equation governs the CO2 flow process in coal matrix with the pressure p as a primary variable.

$$
\frac{\partial v*p}{\partial t}=D \nabla \cdot  (p(\nabla p))
$$

with $$ D=\frac{k}{RTn_0 \eta}  and v=\frac{1}{p+p_0}$$


For more details about the derivation of these equations please refer to: [*"Elastic and Filtration Properties of Coal by Adsorption Test Data Based on Inverse Problem Solution"*
L. A. Nazarov, D.Sc.; L. A. Nazarova, D.Sc.; M. Vandamme, Ph.D.; J-M Pereira, Ph.D.; and I. Tahiri - Poromechanics VI](https://ascelibrary.org/doi/abs/10.1061/9780784480779.034?src=recsys), or feel free to contact me.



<div>
