# Material damage model
**The section illustrates continuum damage model used in the FE-SCA analysis**.  Defining a damage model includes 2 parts: the damage initiation and damage evolution. In the current code, continuum damamge mechanics (CDM) is used to account for the degradation of material properties. The details of the CDM model is illustated in the following sections.

## Damage initiation
The Johnson-Cook criterion is used to define the onset of damage. The Johnson-Cook criterion is a special case of the ductile criterion in which the equivalent plastic strain at the onset of damage, $\epsilon^{cr}$. It is assumed to be of the form
\begin{equation}
 \bar{\varepsilon}_{\mathrm{D}}^{cr}=\left[d_{1}+d_{2} \exp \left(-d_{3} \eta\right)\right]\left[1+d_{4} \ln \left(\frac{\dot{\bar{\varepsilon}}^{p l}}{\dot{\varepsilon}_{0}}\right)\right]\left(1+d_{5} \hat{\theta}\right) 
\end{equation}
where $d_1$-$d_5$ are failure parameters and $\dot{\varepsilon}_{0}$ is the reference strain rate. Note that it is assumed the onset damage strain of fiber material is independent on strain rate and temperature. As a result, $d_4 = d_5 = 0$. $d_1, d_2, d_3$ are input parameters for the material definition. 

$\eta$ is defined as the ratio of pressure and von Mises stress.
\begin{equation}
\eta = \frac{\frac{1}{3}\sigma_{ii}}{\sqrt{\frac{1}{2}S_{ij}S_{ij}}}
\end{equation}
 
## Damage evolution
Exponential law is used to account for the damage evolution. The evolution law can be written as
\begin{equation}
 \begin{array}{lll}d(\varepsilon^{p})=1-\frac{\varepsilon^{cr}}{\varepsilon^{p}} \exp \left(-\alpha(\epsilon^{p}-\varepsilon^{cr})\right) & & \varepsilon^{p} \geq \varepsilon_{0} \\ d(\varepsilon^{p})=0   && \varepsilon^{p}<\varepsilon_{0}\end{array} 
\end{equation}
where $\varepsilon^{p}$ is the equivalent plastic strain, $\varepsilon^{cr}$ the onset damage strain.