---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Introduction to Multiscale simulation
Hierarchical material systems are widespread in nature. A myriad of concurrent simulation techniques has been developed to model the mechanical behavior of hierarchical multiscale materials. In these techniques, the macro-scale simulation can be done using traditional numerical methods such as finite element analysis whereas the micro-scale analysis can use finite element {cite}`feyel2000fe2` or fast Fourier transform-based method{cite}`kochmann2016two`. The total degree of freedom (DOF) of the system equals to DOF of the micro scale multiplied by DOF of the macro scale. As a result, one common drawback of these methods is the exorbitant computational cost, especially when the DOF of the micro scale is large. To this end, various reduced-order modeling techniques have been applied to micro-scale simulation problems to reduce the computational cost {cite}`michel2003nonuniform,yvonnet2007reduced,ladeveze2010latin,liu2016self`. Among them, **Self-consistent clustering analysis (SCA)** is a mechanistic, data-driven method that can model the mechanical response of micro-scale problems while efficiently saving computational time using the $k$-means clustering algorithm. 



```
jupyter-book myst init path/to/markdownfile.md
```

```{bibliography}
```
