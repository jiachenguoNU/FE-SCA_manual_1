# Self-consistent clustering analysis (SCA)

The computational paradigm of SCA mainly consists of 2 stages, namely the offline stage and the online stage. In the offline stage, material points with similar elastic mechanical responses are grouped into the same cluster. The material points are clustered using $k-$ means clustering algorithm based on the strain concentration tensor $\mathbf{A}_{m}(\mathbf{x})$, which is defined as
\begin{equation}
 \boldsymbol{\varepsilon}_{m}(\mathbf{x})=\mathbf{A}_{m}(\mathbf{x}): \boldsymbol{\varepsilon}_{M} 
\end{equation}
where $\boldsymbol{\varepsilon}_{M}$ is the prescribed macroscopic strain along different directions, $\boldsymbol{\varepsilon}_{m}$ is the resultant local strain in the micro-scale level. Note only elastic response is required for the offline computations since we are assuming that the material points having similar mechanical responses in the elastic range should behave similarly in the nonlinear plastic range \cite{liu2016self}. With the obtained strain concentration tensor $\mathbf{A}_{m}(\mathbf{x})$ at each different material point, the whole computational domain can be effectively decomposed by the $k$-means clustering algorithm. Therefore, the number of DOF for the problem can be significantly reduced. \ref{fig:Fig_domain16}(c) and (d)). As shown in Fig. 20, the 45$\times$45 mesh can be decomposed into 12 clusters. Therefore, the total degree of freedom is reduced from 2025 to 12.

% \begin{figure}[hbt!]
% \centering
% \includegraphics[scale=0.7]{FNO2D.eps}
% \caption{An example two-phase composite material for solving Lippmann-Schwinger (LS) equation by SCA and FNO. Each matrix and fiber phases are divided into 16 clusters.}
% \end{figure}
For the clustered material points, we assume the local variable $\beta(x)$ (such as displacement, stress, strain and etc) is uniform inside each cluster. We introduce characteristic function $\chi^I(x)$ in $I-$ th cluster as
\begin{equation}
 \int_{\Omega} \chi^{I}(\mathbf{x})[\bullet] d \mathbf{x} \equiv \int_{\Omega^{I}}[\bullet] d \mathbf{x} 
\end{equation}
Therefore, local variable $\beta(x)$ can be expressed as
\begin{equation}
 \beta(\mathbf{x})=\sum_{I=1}^{k} \beta^{I} \chi^{I}(\mathbf{x}) 
 \label{beta}
\end{equation}
In micromechanics, the linear momentum balance equation can be written as
\begin{equation}
 \frac{\partial \sigma_{i j}(\mathbf{x})}{\partial x_{i}}=0
  \label{equal}
\end{equation}
By assuming a linear elastic reference material with elastic modulus $C^0$, $\sigma_ij$ can be written as
\begin{equation}
 \sigma_ij(x) = C^0 : \epsilon(x) + p(x)
 \label{polarization}
\end{equation}
where $p(x)$ is the polarization stress. Substituting Eq. \ref{polarization} into Eq.\ref{equal}, we have
\begin{equation}
 C_{i j k l}^{0} \frac{\partial \varepsilon_{k l}(\mathbf{x})}{\partial x_{i}}=-\frac{\partial p_{i j}(\mathbf{x})}{\partial x_{i}} 
 \label{pde}
\end{equation}
which is a linear partial differential equation. Using the theory of Green's function, the solution of Eq. \ref{pde} can be written as
\begin{equation}
 \varepsilon(\mathbf{x})+\int_{\Omega} \Phi^{0}\left(\mathbf{x}, \mathbf{x}^{\prime}\right): \mathbf{p}\left(\mathbf{x}^{\prime}\right) d \mathbf{x}^{\prime}-\varepsilon^{0}=0 
 \label{7}
\end{equation}
where $\epsilon_0$ is the homogeneous far-field strain in the reference material. Substituting Eq. \ref{polarization} into Eq. \ref{7}, we have
\begin{equation}
 \varepsilon(\mathbf{x})+\int_{\Omega} \Phi^{0}\left(\mathbf{x}, \mathbf{x}^{\prime}\right):\left[\sigma\left(\mathbf{x}^{\prime}\right)-\mathbf{C}^{0}: \varepsilon\left(\mathbf{x}^{\prime}\right)\right] d \mathbf{x}^{\prime}-\varepsilon^{0}=0
 \label{8}
\end{equation}
which is the so-called Lippmann-Schwinger equation. Since material points have been decomposed into different clusters, the averaged Lippmann-Schwinger equation can be written as
\begin{equation}
 \frac{1}{c^{I}|\Omega|} \int_{\Omega} \chi^{I}(\mathbf{x})  \varepsilon(\mathbf{x}) d \mathbf{x}  +\frac{1}{c^{I}|\Omega|} \int_{\Omega} \int_{\Omega} \chi^{I}(\mathbf{x}) \Phi^{0}\left(\mathbf{x}, \mathbf{x}^{\prime}\right):\left[ \sigma\left(\mathbf{x}^{\prime}\right)-\mathbf{C}^{0}:  \varepsilon\left(\mathbf{x}^{\prime}\right)\right] d \mathbf{x}^{\prime} d \mathbf{x}- \varepsilon^{0}=0 
  \label{9}
\end{equation}

we can obtain the expression for stress and strain using Eq. \ref{beta}
\begin{equation}
 \sigma(\mathbf{x})=\sum_{J=1}^{k} \chi^{J}(\mathbf{x})  \sigma^{J} , \quad  \varepsilon(\mathbf{x})=\sum_{J=1}^{k} \chi^{J}(\mathbf{x})  \varepsilon^{J}
 \label{discretize}
\end{equation}
Substituting Eq. \ref{discretize} into Eq. \ref{9}, we obtain the discretized Lippmann-Schwinger equation and it can be simplified as
\begin{equation}
 \varepsilon^{I}+\sum_{J=1}^{k}\left[\frac{1}{c^{I}|\Omega|} \int_{\Omega} \int_{\Omega} \chi^{I}(\mathbf{x}) \chi^{J}\left(\mathbf{x}^{\prime}\right) \Phi^{0}\left(\mathbf{x}, \mathbf{x}^{\prime}\right) d \mathbf{x}^{\prime} d \mathbf{x}\right]:\left[ \sigma^{J}-\mathbf{C}^{0}: \varepsilon^{J}\right]-\Delta \varepsilon^{0}=0 
\end{equation}
where $C_I$ is the volumn fraction of cluster $I$. The term inside the bracket is defined as the interaction tensors $ \mathbf{D}^{I J}$ 
\begin{equation} \label{Eq 27}
    {D}^{IJ} = \frac{1}{c^{I}|\Omega|} \int_{\Omega} \int_{\Omega}\chi^{I}(x)\chi^{J}(y) \Phi^{0}(x,y)dxdy.
\end{equation}

In the equation, $ \mathbf{D}^{I J}$ is the interaction tensor between $I$th and $J$th clusters. In the online stage, the mechanical response of the microstructure is obtained by solving the incremental form of discretized \textbf{L}ippmann-\textbf{S}chwinger equation.

\begin{equation}
 \Delta \varepsilon^{I}+\sum_{J=1}^{k} \mathbf{D}^{I J}:\left[\Delta \sigma^{J}-\mathbf{C}^{0}: \Delta \varepsilon^{J}\right]-\Delta \varepsilon^{0}=0 
 \label{lp}
\end{equation}
where $\mathbf\Delta \varepsilon^{J}$ and $\mathbf\Delta \sigma^{J}$ are incremental strain and stress in the $J$th cluster; $k$ is the number of clusters; $\mathbf{C}^{0}$ is the reference material stiffness; $\mathbf\Delta \varepsilon^{0}$ is the far-field strain. Note that Eq \ref{lp} is obtained by averaging the stress and strain in each different cluster. Since the number of clusters is far less than the number of DOF of the original system, it can be much faster to solve Eq \ref{lp}. For more details please see \cite{liu2016self}. 

