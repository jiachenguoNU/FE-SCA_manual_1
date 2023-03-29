# Materials
**The section illustrates how to define a material in FE-SCA simulation**. There are 2 options for the FE-SCA. One is the 2-phase simulation that models fiber and matrix. The other one is 3-phase simulation that also considers voids.

The material parameters for fiber and matrix can be either defined in the `Abaqus-CAE user interface` or in the `inp` file. We recommend to define the parameters in the `inp` file.

In the `inp` file, the material parameters are defined in the `** Materials` block, as shown follows.

```none
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
The material parameters defined in the `inp` file include 2 parts, namely parameters for matrix and fiber. The matrix is modeled using isotropic elasto-plastic material law whereas the fiber is modeled using anisotropic elastic material law with continuum damage.

## Defining material parameters for matrix
The material parameters for matrix include elastic modulus $E_m$, Possion's ratio $\nu_m$ and hardening curve. In this example, $E_m = 3760 $MPa and $\nu_m = 0.39$.

Note that the hardening curve has to be defined in the `VUMAT` subroutine instead of the `inp` file. To modify the hardening curve, users need to open the `VUMAT` subroutine and navigate to `subroutine uhardening` section. The hardening curve is defined using the code as shown below. `table(1,:)` refers to the yield stress $\sigma_y$ for different equivalent plastic strain $\epsilon_p$. `table(2,:)` refers to the corresponding equivalent plastic strain amplitude. Users can add more data points to the yield curve by adding more columns for the table. 
```none
C set yield stress to last value of table, hardening to zero
C

      table(1,:)=(/2.0, 2.01/)
      table(2,:)=(/0.0, 0.001/)
      syield=table(1, 1)
      hard = zero
```


## Defining material parameters for fiber
The material properties for fiber is modeled using the orthotropic elastic material law with continuum damage. There are 9 parameters to define the anisotropic elastic material properties, namely, $E_11$, $E_22$, $E_33$, $G_12$, $G_13$, $G_23$, $\nu_12$, $\nu_13$ and $\nu_23$ (it is assumed that $\nu_{ij} = \nu_{ji}$). The continuum damage model requires to define 5 parameters (theory of the continuum damage model used).