# Installation Guide
This guide shows the steps to install FE-SCA on your PC. FE-SCA requires 3 different software packages, i.e., **ABAQUS (FE Anylasis), Intel Fortran Compiler (VUMAT for SCA), User Interface (Microstructure reconstruction and inp file generator)**

## Installation of ABAQUS
**Abaqus FEA** (formerly ABAQUS) is a suite of software tools used for finite element analysis and computer-aided engineering. It was first released in 1978 and is named after the abacus calculation tool, as reflected in its logo. The Abaqus product suite comprises five core software products.

One of these products is Abaqus/CAE, which stands for "Complete Abaqus Environment" and is a software application used for both pre-processing (modeling and analysis of mechanical components and assemblies) and post-processing (visualizing the finite element analysis result). Abaqus/Viewer is a subset of Abaqus/CAE that includes only the post-processing module and can be launched independently.

Another product is Abaqus/Standard, which is a general-purpose finite-element analyzer that uses an implicit integration scheme (traditional) to solve problems.

Abaqus/Explicit is a finite-element analyzing tool that uses an explicit integration scheme to solve equations of nonlinear systems with complex contacts under transient loads.
```{seealso}
See the official webpage of [ABAQUS](https://www.3ds.com/products-services/simulia/products/abaqus/) for more details.
```

## Installation of Intel Fortran Compiler
**Intel Fortran Compiler**, as part of Intel OneAPI HPC toolkit, is a group of Fortran compilers from Intel for Windows, macOS, and Linux. Since ABAQUS uses Fortran as its default language for user subroutine, Intel Fortran Compiler is required to run user subrountines. 
```{seealso}
See the official webpage of [Intel oneAPI](https://www.intel.com/content/www/us/en/developer/tools/oneapi/toolkits.html#gs.qyhlgt) for more details.
```
```{note}
See [this webpage](https://community.intel.com/t5/Intel-Fortran-Compiler/Linking-Fortran-compiler-with-Abaqus-minimal-required/td-p/1361849) for step-by-step installation details to link ABAQUS with Intel Fortran Compiler
```

## Installation of User Interface