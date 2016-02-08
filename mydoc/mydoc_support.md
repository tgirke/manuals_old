---
title: Support
tags: [getting_started]
keywords: questions, troubleshooting, contact, support
last_updated: November 30, 2015
summary: "longevity main vignette."
---


# Introduction 
This vignette provides general information about the `longevityTools` package.
This includes an introduction into the objects, data structures, methods and
functions defined by `longevityTools`. The development of `longevityTools` is part of the 
[Longevity Genomics](http://www.longevitygenomics.org/) project. 
The analysis workflows used by this project are documented in its companion vignettes listed below.
$$eSNP Risk Score_i = \sum_{j=1}^{N} eSNP_j^{AlleleDown} + \sum_{k=1}^{N} eSNP_k^{AlleleUp}$$


# Getting Started

## Installation

The R software for running [_`longevityTools`_](https://github.com/tgirke/longevityTools) can be downloaded from [_CRAN_](http://cran.at.r-project.org/). The _`longevityTools`_ package can be installed from the R console using the following _`biocLite`_ install command. 


{% highlight rb %}
source("http://bioconductor.org/biocLite.R") # Sources the biocLite.R installation script 
biocLite("tgirke/longevityTools", build_vignettes=TRUE, dependencies=TRUE) # Installs package from GitHub
{% endhighlight %}

## Loading package and documentation

{% gist c26daac0f647f1732a58 %} 

{% highlight s %}
library("longevityTools") # Loads the package
library(help="longevityTools") # Lists package info
vignette("longevityTools") # Opens vignette
{% endhighlight %}


# Overview of object clases, methods and functions

To be continued... [@Lamb2006-uv; @Peters2015-fc; @Sood2015-pb].

# Workflow vignettes

Currently, this package includes the following analysis workflow vignettes:

* [longevityTools](https://htmlpreview.github.io/?https://github.com/tgirke/longevityTools/blob/master/vignettes/longevityTools.html): overview vignette
* [longevityTools_eQTL](https://htmlpreview.github.io/?https://github.com/tgirke/longevityTools/blob/master/vignettes/longevityTools_eQTL.html): eQTL, eSNP and GWAS analysis
* [longevityTools_CMAP](https://htmlpreview.github.io/?https://github.com/tgirke/longevityTools/blob/master/vignettes/longevityTools_CMAP.html): connecting drug- and age-related gene expression signatures
* longevityTools_Drugs: coming soon

<div align="right">[Back to Table of Contents]()</div>

# Funding
This project is funded by NIH grant U24AG051129 awarded by the National Intitute of Aging (NIA).

# Introduction 
This vignette is part of the NIA funded Longevity Genomics project. For more information on this project please visit its
website [here](http://www.longevitygenomics.org/projects/). The GitHub repository of the corresponding R package
is available <a href="https://github.com/tgirke/longevityTools">here</a> and the most recent version of this
vignette can be found <a href="https://htmlpreview.github.io/?https://github.com/tgirke/longevityTools/blob/master/vignettes/longevityTools_eQTL.html">here</a>.

Based on muscle gene expression from 15 young (25 year old) and 15 old (65 year old) participants, Sood et al. identified a 150 probe set that accurately classified young and old individuals in external studies w
ith gene expression data collected from tissues other than muscle [@Sood2015-pb]. A gene score based on the classifier was associated with better renal function, increased survival time over follow-up, and decreased Alzheimer's Disease prevalence.

Our goal is to perform Mendelian Randomization using the 150 gene set to determine whether SNPs associated with expression (eSNPs) of the 150 genes are associated with the aging phenotypes identified by Sood et al.

Hypothesis: eSNPs associated with younger expression profile are markers for younger biological age relative to chronological age, which would be associated with longevity.

<div align="right">[Back to Table of Contents]()</div>

# General Analytical Approach

## Construction of MR eSNP risk score

File sood-2015-fileS1.xls reports the expression direction relative to age for each probe from the 150 probe set. See Top 150 worksheet. A gene marked as 'down' in column 'Ratio of Y:O muscle' means that the expression of the gene is lower in young vs old muscle. 

The goal is to generate an eSNP risk score constructed from eSNP alleles associated with increasing gene expression for genes that decrease with age and from eSNP alleles associated with decreasing gene expression for genes that increase with age. This eSNP risk score would represent an expression profile that more closely mimics the younger age profile rather than the older age profile.

For the 150 probes that map to genes, identify cis-eSNPs using GTEx preanalyzed results from whole blood. Preanalyzed GTEx results correct for multiple testing of SNPs for each gene. To identify independent cis-eSNPs for each gene, prune cis-eSNPs in LD using 1000G EUR population group genotypes. Once independent cis-eSNPs are identified, create a file listing the SNPs to be included in a risk score and which allele is associated with decreasing expression for genes that increase with age (upregulated gene) and which allele is associated with increasing expression for genes that decrease with age (downregulated gene). Upregulated and downregulated genes based on column 'Ratio of Y:O muscle' from Sood et al supplemental file.

Individual level eSNP risk scores will be constructed as below. The eSNP risk score represents the MR instrumental variable.

$$ eSNP Risk Score_i = \sum_{j=1}^{N} eSNP_j^{AlleleDown} + \sum_{k=1}^{N} eSNP_k^{AlleleUp}  $$




# Version information


{% highlight s %}
sessionInfo()
{% endhighlight %}

{% highlight s %}
## R version 3.2.3 (2015-12-10)
## Platform: x86_64-pc-linux-gnu (64-bit)
## Running under: Ubuntu 14.04.3 LTS
## 
## locale:
##  [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C               LC_TIME=en_US.UTF-8       
##  [4] LC_COLLATE=en_US.UTF-8     LC_MONETARY=en_US.UTF-8    LC_MESSAGES=en_US.UTF-8   
##  [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                  LC_ADDRESS=C              
## [10] LC_TELEPHONE=C             LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       
## 
## attached base packages:
## [1] stats     graphics  utils     datasets  grDevices methods   base     
## 
## other attached packages:
## [1] ggplot2_2.0.0        longevityTools_1.0.0 BiocStyle_1.8.0     
## 
## loaded via a namespace (and not attached):
##  [1] Rcpp_0.12.3      codetools_0.2-14 digest_0.6.9     plyr_1.8.3       grid_3.2.3      
##  [6] gtable_0.1.2     formatR_1.2.1    magrittr_1.5     evaluate_0.8     scales_0.3.0    
## [11] stringi_1.0-1    rmarkdown_0.9.2  tools_3.2.3      stringr_1.0.0    munsell_0.4.2   
## [16] yaml_2.1.13      colorspace_1.2-6 htmltools_0.3    knitr_1.12
{% endhighlight %}

