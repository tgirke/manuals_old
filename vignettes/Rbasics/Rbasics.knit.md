---
title: "Introduction to R" 
author: "Author: Thomas Girke"
date: "Last update: 07 February, 2016" 
output:
  BiocStyle::html_document:
    toc: true
    toc_depth: 3
    fig_caption: yes

fontsize: 14pt
---
<!--
%% \VignetteEngine{knitr::rmarkdown}
%\VignetteIndexEntry{Overview Vignette}
%% \VignetteDepends{methods}
%% \VignetteKeywords{compute cluster, pipeline, reports}
%% \VignettePackage{longevityTools}
-->

<!---
- Compile from command-line
echo "rmarkdown::render('Rbasics.Rmd', clean=F)" | R -slave; R CMD Stangle Rbasics.Rmd

- Commit to github
git commit -am "some edits"; git push -u origin master

- To customize font size and other style features, add this line to output section in preamble:  
    css: style.css
-->

<script type="text/javascript">
document.addEventListener("DOMContentLoaded", function() {
  document.querySelector("h1").className = "title";
});
</script>
<script type="text/javascript">
document.addEventListener("DOMContentLoaded", function() {
  var links = document.links;  
  for (var i = 0, linksLength = links.length; i < linksLength; i++)
    if (links[i].hostname != window.location.hostname)
      links[i].target = '_blank';
});
</script>



# Introduction 

[R](http://cran.at.r-project.org) is a powerful statistical environment and
programming language for data analysis and visualization. The associated
[Bioconductor](http://bioconductor.org/) and CRAN package repositories provide
many additional R packages for statistical data analysis for a wide array of 
research areas, such as tools for big data and genome analysis. The R software 
is free and runs on all common operating systems. 

## Look and Feel of the R Environment

### Why Using R?
* Complete statistical environment and programming language
* Efficient functions and data structures for data analysis
* Powerful graphics
* Access to fast growing number of analysis packages
* Most widely used language in bioinformatics
* Is standard for data mining and biostatistical analysis
* Technical advantages: free, open-source, available for all OSs

### Books and Documentation
* simpleR - Using R for Introductory Statistics (John Verzani, 2004) \href{http://cran.r-project.org/doc/contrib/Verzani-SimpleR.pdf}{{\beamerbutton{Link}}}
* Bioinformatics and Computational Biology Solutions Using R and Bioconductor (Gentleman et al., 2005) \href{http://www.bioconductor.org/help/publications/books/bioinformatics-and-computational-biology-solutions/}{{\beamerbutton{Link}}}
* More on this see "Finding Help" section in UCR Manual \href{http://manuals.bioinformatics.ucr.edu/home/R\_BioCondManual\#TOC-Finding-Help}{{\beamerbutton{Link}}}

### Working environments (IDEs) for R
<center><img title="R_Interfaces" src="images/rinterface.png"/></center>
<center> R Projects and Interfaces</center>

Some R working environments with support for syntax highlighting and utilities to send code 
to the R console: 

* [RStudio](https://www.rstudio.com/products/rstudio/features): excellent choice for beginners ([Cheat Sheet](http://www.rstudio.com/wp-content/uploads/2016/01/rstudio-IDE-cheatsheet.pdf)) 
* Basic R code editors provided by Rguis 
* [gedit](https://wiki.gnome.org/Apps/Gedit), [Rgedit](http://rgedit.sourceforge.net/), [RKWard](https://rkward.kde.org/), [Eclipse](http://www.walware.de/goto/statet), [Tinn-R](http://www.sciviews.org/Tinn-R/), [Notepad++](https://notepad-plus-plus.org/), [NppToR](http://sourceforge.net/projects/npptor/)
* [Vim-R-Tmux](http://manuals.bioinformatics.ucr.edu/home/programming-in-r/vim-r): R working environment based on vim and tmux 
* [Emacs](http://www.xemacs.org/Download/index.html) ([ESS add-on package](http://ess.r-project.org/))
	
#### Example: RStudio 

New integrated development environment (IDE) for [R](http://www.rstudio.com/ide/download/). Highly functional for both beginners and 
advanced.
<center><img title="RStudio" src="images/rstudio.png"/></center>
<center> RStudio IDE</center>
Some userful shortcuts: `Ctrl+Enter` (send code), `Ctrl+Shift+C` (comment/uncomment), `Ctrl+1/2` (switch window focus)

#### Example: Vim-R-Tmux: Command-Line IDE for R

Terminal-based Working Environment for R: [Vim-R-Tmux](http://manuals.bioinformatics.ucr.edu/home/programming-in-r/vim-r)
<center><img title="Vim-R-Tmux" src="images/screenshot.png" width="65%" height="65%" ></center>
<center>Vim-R-Tmux IDE for R</center>

### Package Repositories

* CRAN ($>$6,000 packages) general data analysis \href{http://cran.at.r-project.org/}{{\beamerbutton{Link}}}
* Bioconductor ($>$900 packages) bioscience data analysis \href{http://www.bioconductor.org/}{{\beamerbutton{Link}}}
* Omegahat ($>$90 packages) programming interfaces \href{http://www.omegahat.org/}{{\beamerbutton{Link}}}

## Installation of R and Add-on Packages

1. Install R for your operating system from [CRAN](http://cran.at.r-project.org/).

2. Install RStudio from [RStudio](http://www.rstudio.com/ide/download).

3. Install CRAN Packages from R console like this:

    
    ```r
    install.packages(c("pkg1", "pkg2")) 
    install.packages("pkg.zip", repos=NULL)
    ```

4. Install Bioconductor packages as follows:

    
    ```r
    source("http://www.bioconductor.org/biocLite.R")
    library(BiocInstaller)
    BiocVersion()
    biocLite()
    biocLite(c("pkg1", "pkg2"))
    ```

5. For more details consult the [Bioc Install page](\href{http://www.bioconductor.org/install/)
and [BiocInstaller](http://www.bioconductor.org/packages/release/bioc/html/BiocInstaller.html) package.

Plotting example

```r
barplot(1:10, col="green")
```

![](Rbasics_files/figure-html/plot_example-1.png)\




```r
sessionInfo()
```

```
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
## [1] ggplot2_2.0.0   limma_3.26.3    BiocStyle_1.8.0
## 
## loaded via a namespace (and not attached):
##  [1] Rcpp_0.12.3      codetools_0.2-14 digest_0.6.9     plyr_1.8.3       grid_3.2.3      
##  [6] gtable_0.1.2     formatR_1.2.1    magrittr_1.5     evaluate_0.8     scales_0.3.0    
## [11] stringi_1.0-1    rmarkdown_0.9.2  tools_3.2.3      stringr_1.0.0    munsell_0.4.2   
## [16] yaml_2.1.13      colorspace_1.2-6 htmltools_0.3    knitr_1.12
```

