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

# Multiscale simulation
Hierarchical material systems are widespread in nature. A myriad of concurrent simulation techniques has been developed to model the mechanical behavior of hierarchical multiscale materials. In these techniques, the macro-scale simulation can be done using traditional numerical methods such as finite element analysis whereas the micro-scale analysis can use finite element {cite}`feyel2000fe2` or fast Fourier transform-based method{cite}`kochmann2016two`. The total degree of freedom (DOF) of the system equals to DOF of the micro scale multiplied by DOF of the macro scale. As a result, one common drawback of these methods is the exorbitant computational cost, especially when the DOF of the micro scale is large. To this end, various reduced-order modeling techniques have been applied to micro-scale simulation problems to reduce the computational cost {cite}`michel2003nonuniform,yvonnet2007reduced,ladeveze2010latin,liu2016self`. Among them, Self-consistent clustering analysis (SCA) is a mechanistic, data-driven method that can model the mechanical response of micro-scale problems while efficiently saving computational time using the $k$-means clustering algorithm. 

```{code-cell}
print(2 + 2)
print('Hello World')
```

When your book is built, the contents of any `{code-cell}` blocks will be
executed with your default Jupyter kernel, and their outputs will be displayed
in-line with the rest of your content.

```{seealso}
Jupyter Book uses [Jupytext](https://jupytext.readthedocs.io/en/latest/) to convert text-based files to notebooks, and can support [many other text-based notebook files](https://jupyterbook.org/file-types/jupytext.html).
```

## Create a notebook with MyST Markdown

MyST Markdown notebooks are defined by two things:

1. YAML metadata that is needed to understand if / how it should convert text files to notebooks (including information about the kernel needed).
   See the YAML at the top of this page for example.
2. The presence of `{code-cell}` directives, which will be executed with your book.

That's all that is needed to get started!

## Quickly add YAML metadata for MyST Notebooks

If you have a markdown file and you'd like to quickly add YAML metadata to it, so that Jupyter Book will treat it as a MyST Markdown Notebook, run the following command:

```
jupyter-book myst init path/to/markdownfile.md
```

```{bibliography}
```
