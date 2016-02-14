---
title: ChemmineR - Cheminformatics Toolkit for R
keywords: 
last_updated: Sat Feb 13 17:50:15 2016
---
Authors: Kevin Horan, Yiqun Cao, Tyler Backman, [Thomas Girke](mailto:thomas.girke@ucr.edu)

Last update: 13 February, 2016 



## Introduction

`ChemmineR` is a cheminformatics package for analyzing
drug-like small molecule data in R. Its latest version contains
functions for efficient processing of large numbers of small molecules,
physicochemical/structural property predictions, structural similarity
searching, classification and clustering of compound libraries with a
wide spectrum of algorithms.

![Figure: `ChemmineR` environment with its add-on packages and
selected functionalities](overview.png )

In addition, `ChemmineR` offers visualization functions
for compound clustering results and chemical structures. The integration
of chemoinformatic tools with the R programming environment has many
advantages, such as easy access to a wide spectrum of statistical
methods, machine learning algorithms and graphic utilities. The first
version of this package was published in Cao et al. [-@Cao_2008]. Since then many additional
utilities and add-on packages have been added to the environment (Figure 2) and
many more are under development for future releases [@Backman_2011; @Wang_2013].



__Recently Added Features__

-   Improved SMILES support via new `SMIset` object class
    and SMILES import/export functions

-   Integration of a subset of OpenBabel functionalities via new
    `ChemmineOB` add-on package [@Cao_2008]

-   Streaming functionality for processing millions of molecules on a
    laptop

-   Mismatch tolerant maximum common substructure (MCS) search algorithm

-   Fast and memory efficient fingerprint search support using atom pair
    or PubChem fingerprints


