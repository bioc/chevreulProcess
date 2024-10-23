
<!-- README.md is generated from README.Rmd. Please edit that file -->

# chevreulProcess

This package includes a set of Shiny apps for exploring single cell RNA
datasets processed as a SingleCellExperiment

A demo using a human gene transcript dataset from Shayler et al. (link)
is available
<a href="http://cobrinik-1.saban-chla.usc.edu:8080/app/objectApp" target="_blank" rel="noopener noreferrer">here</a>

There are also convenient functions for:

- Clustering and Dimensional Reduction of Raw Sequencing Data.
- Integration and Label Transfer
- Louvain Clustering at a Range of Resolutions
- Cell cycle state regression and labeling

> \[!WARNING\] chevreulProcess was designed for full-length smart-seq
> based single cell data. Default settings may not be appropriate for
> droplet (10x) data, though most can be adjusted. Keep in mind best
> practices regarding normalization, dimensional reduction, etc. when
> using.

## Installation

You can install the released version of chevreulProcess from
<a href="https://github.com/whtns/chevreulProcess" target="_blank" rel="noopener noreferrer">github</a>
with:

### Install locally and run in three steps:

You can install chevreulProcess locally using the following steps:

``` r
install.packages("devtools")
devtools::install_github("whtns/chevreulProcess")
chevreulProcess::create_project_db()
```

You can also customize the location of the app using these steps:

``` r
devtools::install_github("whtns/chevreulProcess")
chevreulProcess::create_project_db(destdir = "/your/path/to/app")
```

## Getting Started

First, load chevreulProcess and all other packages required

``` r
library(chevreulProcess)
library(SingleCellExperiment)
library(tidyverse)
library(ggraph)
```

## TLDR

chevreulProcess provides a single command to:

- construct a SingleCellExperiment object

- filter genes by minimum expression and ubiquity

- normalize and scale expression by any of several methods packaged in
  SingleCellExperiment

## Run clustering on a single object

By default clustering will be run at ten different resolutions between
0.2 and 2.0. Any resolution can be specified by providing the resolution
argument as a numeric vector.

``` r
clustered_sce <- sce_process(chevreul_sce,
    experiment_name = "sce_hu_trans",
    organism = "human"
)
```
