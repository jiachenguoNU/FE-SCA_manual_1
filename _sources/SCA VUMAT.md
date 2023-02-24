# SCA VUMAT

```{code-cell}
**  Materials
*Material, name=SCA1
*Density
10
*Damping,alpha=0.1
*User Material, constants=24
**Em,  vm,  E11, E22, E33, v12, v13, v23
3.76e3, 0.39, 138.8e3, 7.08e3, 7.08e3, 0.25, 0.25, 0.31
**G12,G13,G23,  E0,   v0, ecr1, ecr2, ecr3
4.49e3, 4.49e3,  4.49e3, 4.49e3, 0.39, 0.5, 0., 0
** alpha(evolution rate of the damage parameter), rve_dmg, SC,  gammastep, clc_o,   not_used, not_used, not_used
   500,    200,   1.0  , 0.5,  100000.0, 14,      89,      89
** Number of state variables 10*Np+5
*Depvar, delete=517
700
```