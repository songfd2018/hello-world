# Batch Effects Correction With Unknow Subtypes for scRNA-seq Data (BUSseq)

## Contents

- [Overview](#overview)
- [Repo Contents](#repo-contents)
- [System Requirements](#system-requirements)
- [Installation Guide](#installation-guide)
- [Demo](#demo)
- [Instructions for use](#instructions-for-use)
- [License](./LICENSE)
- [Citation](#citation)

# Overview
Single-cell RNA-sequencing (scRNA-seq) technologies enable the measurement of the transcriptome of individual cells, which provides unprecedented opportunities to discover cell types and understand cellular heterogeneity. Despite their widespread applications, single-cell RNA-sequencing (scRNA-seq) experiments are still plagued by batch effects and dropout events.

One of the major tasks of scRNA-seq experiments is to identify cell types for a population of cells. Therefore, the cell type of each individual cell is always unknown and is the target of inference. However, most existing methods for batch effects correction, such as Combat space and the surrogate variable analysis (SVA), are designed for bulk experiments and require knowledge of the subtype information, which corresponds to cell type information for scRNA-seq data, of each sample a priori.
  
Here, the R package `BUSseq` fits an interpretable Bayesian hierarchical model---the Batch Effects Correction with Unknown Subtypes for scRNA seq Data(BUSseq)---to correct batch effects in the presence of unknown cell types. BUSseq is able to simultaneously correct batch effects, clusters cell types, and takes care of the count data nature, the overdispersion, the dropout events, and the cell-specific sequencing depth of scRNA-seq data. After correcting the batch effects with BUSseq, the corrected value can be used for downstream analysis as if all cells were sequenced in a single batch. BUSseq can integrate the read count matrices measured from different platforms and allow cell types to be measured in some but not all of the batches as long as the experimental design fulfills the conditions listed in our [manuscript](https://www.biorxiv.org/content/10.1101/533372v1).

# Repo Contents

- [R](./R): `R` package code.
- [inst/doc](./inst/doc): package pdf user's guide, and usage of the `BUSseq` package on a small example dataset.
- [man](./man): package manual for help in R session.
- [tests](./tests): `R` unit tests written using the `testthat` package.
- [vignettes](./vignettes): `R` vignettes for R session html help pages.

# System Requirements

## Hardware Requirements

The `BUSseq` package requires only a standard computer with enough RAM to support the operations defined by a user. For minimal performance, this will be a computer with about 2 GB of RAM. For optimal performance, we recommend a computer with the following specs:

RAM: 16+ GB  
CPU: 2+ cores, 3.3+ GHz/core

The runtimes below are generated using a computer with Windows 10 operating system, the recommended specs (16 GB RAM, 2 cores@3.4 GHz) and internet of speed 25 Mbps.

## Software Requirements

### OS Requirements

This package is supported for *Linux* operating systems. The package has been tested on the following systems:

Linux: Ubuntu 16.04

Mac OSX: Mac OS X 10.14 Mojave

Windows: Windows 10

The `BUSseq` package should be compatible with *Windows*, *Mac*, and *Linux* operating systems.

### Software dependencies

Before setting up the `BUSseq` package, users should have `R` version 3.5.0 or higher, and several packages set up from CRAN.

#### Installing R version 3.5.2 on Windows

Please download [R-3.5.2 for Windows] (https://cran.r-project.org/bin/windows/base/) and double click to install it on your computer. It will take a few minutes.

#### Package dependencies

Users should install the following packages prior to installing `BUSseq`, from an `R` session:

```
install.packages(c('devtools', 'bigmemory', 'gplots', 'knitr'))
```

which will install in 10 seconds on a recommended machine.

#### Package Versions

The `BUSseq` package functions with all packages in their latest versions as they appear on `CRAN` on February 13, 2019. Users can check [the Comprehensive R Archive Network] (https://cran.r-project.org/) for details. The versions of software are, specifically:
```
devtools: 2.0.1
bigmemory: 4.5.33
gplots: 3.0.1.1
knitr: 1.12
```

If you are having an issue that you believe to be tied to software versioning issues, please drop us an [Issue](https://github.com/songfd2018/BUSseq/issues). 

# Installation Guide

From an `R` session, type:

```
require(devtools)
install_github("songfd2018/BUSseq", build_vignettes = TRUE) # install BUSseq
```

or

```
install.packages("/your/location/directory/BUSseq_0.99.6.tar.gz", repos = NULL, type = "source") # install BUSseq from zip file
```
The package should take approximately 25 seconds from Github or 8 seconds from the compiled package to install on a recommended computer. 

# Demo
Please see the vignettes for help using the package:

```
vignette("BUSseq_user_guide",package="BUSseq")  # view the vignettes
```

It will take about 6 minutes to run the first six sections in the vignettes except the last section, Model Selection using BIC. In the last section, we repeat the fitting with different numbers of cell types to attain the minimum BIC. Thus, 5 more of 6-minute are required to implement the model selection. In general, we parallel the codes for different numbers of cell types.

Actually, the package can also record the time of conducting MCMC algorithm, adjusting raw count data and calculating the BIC value, respectively, which you can find in the vignette. When generating the vignette, we use another computer with Ubuntu 18.04 operating system, 8 GB RAM and 8 cores@2.60 GHz, so the running time is faster than that on a recommended computer.

# Instructions for use
Please follow the steps in the [BUSseq implementation](https://github.com/songfd2018/BUSseq_implementation) repository to reproduce all the results and figures of simulation and real data analysis.

# Citation
BUSseq manuscript is available from [bioRxiv](https://www.biorxiv.org/content/10.1101/533372v1). If you use BUSseq for your work, please cite our paper.

		@article {Song533372,
			author = {Song, Fangda and Chan, Ga Ming and Wei, Yingying},
			title = {Flexible Experimental Designs for Valid Single-cell RNA-sequencing Experiments Allowing Batch Effects Correction},
			elocation-id = {533372},
			year = {2019},
			doi = {10.1101/533372},
			publisher = {Cold Spring Harbor Laboratory},
			URL = {https://www.biorxiv.org/content/early/2019/01/29/533372},
			eprint = {https://www.biorxiv.org/content/early/2019/01/29/533372.full.pdf},
			journal = {bioRxiv}
		}
