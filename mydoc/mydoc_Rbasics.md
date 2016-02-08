---
title: Introduction
keywords: documentation theme, jekyll, technical writers, help authoring tools, hat replacements
last_updated: February 06, 2016
tags: [getting_started]
summary: "Introduction to the statistical programming environment R."
---

[ [View R markdown](http://girke.bioinformatics.ucr.edu/manuals/vignettes/Rbasics/Rbasics.html) ] 
[ [Download *.Rmd](http://girke.bioinformatics.ucr.edu/manuals/vignettes/Rbasics/Rbasics.Rmd) ]
[ [Download *.R](http://girke.bioinformatics.ucr.edu/manuals/vignettes/Rbasics/Rbasics.R) ]

# Introduction 

[R](http://cran.at.r-project.org) is a powerful statistical environment and
programming language for the analysis and visualization of any type of data.
The associated [Bioconductor](http://bioconductor.org/) and CRAN package
repositories provide many additional R packages for statistical data analysis
for a wide array of research areas, such as tools for big data and genome
analysis. The R software is free and runs on all common operating systems. 

## Look and Feel of R Environment

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
<center><img title="R_Interfaces" src="images/vignette_Rbasics//rinterface.png"/></center>
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

<center><img title="RStudio" src="images/vignette_Rbasics//rstudio.png"/></center>
<center> RStudio IDE</center>

Some userful shortcuts: `Ctrl+Enter` (send code), `Ctrl+Shift+C` (comment/uncomment), `Ctrl+1/2` (switch window focus)

#### Example: Vim-R-Tmux

Terminal-based Working Environment for R: [Vim-R-Tmux](http://manuals.bioinformatics.ucr.edu/home/programming-in-r/vim-r)

<center><img title="Vim-R-Tmux" src="images/vignette_Rbasics//screenshot.png" ></center>
<center>Vim-R-Tmux IDE for R</center>

## R Package Repositories

* CRAN (>8,000 packages) general data analysis \href{http://cran.at.r-project.org/}{{\beamerbutton{Link}}}
* Bioconductor (>1,100 packages) bioscience data analysis \href{http://www.bioconductor.org/}{{\beamerbutton{Link}}}
* Omegahat (>90 packages) programming interfaces \href{http://www.omegahat.org/}{{\beamerbutton{Link}}}

## Installation of R and Add-on Packages

1. Install R for your operating system from [CRAN](http://cran.at.r-project.org/).

2. Install RStudio from [RStudio](http://www.rstudio.com/ide/download).

3. Install CRAN Packages from R console like this:


{% highlight s %}
install.packages(c("pkg1", "pkg2")) 
install.packages("pkg.zip", repos=NULL)
{% endhighlight %}

4. Install Bioconductor packages as follows:


{% highlight s %}
source("http://www.bioconductor.org/biocLite.R")
library(BiocInstaller)
BiocVersion()
biocLite()
biocLite(c("pkg1", "pkg2"))
{% endhighlight %}

5. For more details consult the [Bioc Install page](\href{http://www.bioconductor.org/install/)
and [BiocInstaller](http://www.bioconductor.org/packages/release/bioc/html/BiocInstaller.html) package.

## Getting Around

### Startup and Closing Behavior

* __Starting R__:
    The R GUI versions, including RStudio, under Windows and Mac OS X can be
    opened by double-clicking their icons. Alternatively, one can start it by
    typing `R` in a terminal (default under Linux). 

* __Startup/Closing Behavior__:
    The R environment is controlled by hidden files in the startup directory:
    `.RData`, `.Rhistory` and `.Rprofile` (optional). 
	
    
* __Closing R__:

    
    {% highlight s %}
    q()  
    Save workspace image? [y/n/c]:
    {% endhighlight %}
        
* __Note__:
    When responding with `y`, then the entire R workspace will be written to
    the `.RData` file which can become very large. Often it is sufficient to just
    save an analysis protocol in an R source file. This way one can quickly
    regenerate all data sets and objects. 


### Navigating directories

Create an object with the assignment operator `<-` or `=`

{% highlight s %}
object <- ...
{% endhighlight %}

List objects in current R session

{% highlight s %}
ls()
{% endhighlight %}

Return content of current working directory

{% highlight s %}
dir()
{% endhighlight %}

Return path of current working directory

{% highlight s %}
getwd()
{% endhighlight %}

Change current working directory

{% highlight s %}
setwd("/home/user")
{% endhighlight %}

## Basic Syntax

General R command syntax


{% highlight s %}
object <- function_name(arguments) 
object <- object[arguments] 
{% endhighlight %}

Finding help


{% highlight s %}
?function_name
{% endhighlight %}

Load a library/package


{% highlight s %}
library("my_library") 
{% endhighlight %}

List functions defined by a library


{% highlight s %}
library(help="my_library")
{% endhighlight %}

Load library manual (PDF or HTML file)


{% highlight s %}
vignette("my_library") 
{% endhighlight %}

Execute an R script from within R


{% highlight s %}
source("my_script.R")
{% endhighlight %}

Execute an R script from command-line (the first of the three options is preferred)


{% highlight sh %}
$ Rscript my_script.R
$ R CMD BATCH my_script.R 
$ R --slave < my_script.R 
{% endhighlight %}

## Data Types 

__Numeric data__: `1, 2, 3, ...`


{% highlight s %}
x <- c(1, 2, 3); x
is.numeric(x)
as.character(x)
{% endhighlight %}

__Character data__: `"a", "b", "c", ...`


{% highlight s %}
x <- c("1", "2", "3"); x
is.character(x)
as.numeric(x)
{% endhighlight %}

__Complex data__: mix of both


{% highlight s %}
c(1, "b", 3)
{% endhighlight %}

__Logical data__: `TRUE` of `FALSE`


{% highlight s %}
x <- 1:10 < 5
x  
{% endhighlight %}

{% highlight s %}
##  [1]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
{% endhighlight %}

{% highlight s %}
!x
{% endhighlight %}

{% highlight s %}
##  [1] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
{% endhighlight %}

{% highlight s %}
which(x) # Returns index for the 'TRUE' values in logical vector
{% endhighlight %}

{% highlight s %}
## [1] 1 2 3 4
{% endhighlight %}

## Data Objects

__Vectors (1D)__: `numeric` or `character`


{% highlight s %}
myVec <- 1:10; names(myVec) <- letters[1:10]  
myVec[1:5]
{% endhighlight %}

{% highlight s %}
## a b c d e 
## 1 2 3 4 5
{% endhighlight %}

{% highlight s %}
myVec[c(2,4,6,8)]
{% endhighlight %}

{% highlight s %}
## b d f h 
## 2 4 6 8
{% endhighlight %}

{% highlight s %}
myVec[c("b", "d", "f")]
{% endhighlight %}

{% highlight s %}
## b d f 
## 2 4 6
{% endhighlight %}

__Factors (1D)__: vectors with grouping information


{% highlight s %}
factor(c("dog", "cat", "mouse", "dog", "dog", "cat"))
{% endhighlight %}

{% highlight s %}
## [1] dog   cat   mouse dog   dog   cat  
## Levels: cat dog mouse
{% endhighlight %}

__Matrices (2D)__: two dimensional structures with data of same type


{% highlight s %}
myMA <- matrix(1:30, 3, 10, byrow = TRUE) 
class(myMA)
{% endhighlight %}

{% highlight s %}
## [1] "matrix"
{% endhighlight %}

{% highlight s %}
myMA[1:2,]
{% endhighlight %}

{% highlight s %}
##      [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
## [1,]    1    2    3    4    5    6    7    8    9    10
## [2,]   11   12   13   14   15   16   17   18   19    20
{% endhighlight %}

{% highlight s %}
myMA[1, , drop=FALSE]
{% endhighlight %}

{% highlight s %}
##      [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
## [1,]    1    2    3    4    5    6    7    8    9    10
{% endhighlight %}

__Data Frames (2D)__: two dimensional objects with data of variable types


{% highlight s %}
myDF <- data.frame(Col1=1:10, Col2=10:1) 
myDF[1:2, ]
{% endhighlight %}

{% highlight s %}
##   Col1 Col2
## 1    1   10
## 2    2    9
{% endhighlight %}

__Arrays__: data structure with one, two or more dimensions


__Lists__: containers for any object type


{% highlight s %}
myL <- list(name="Fred", wife="Mary", no.children=3, child.ages=c(4,7,9)) 
myL
{% endhighlight %}

{% highlight s %}
## $name
## [1] "Fred"
## 
## $wife
## [1] "Mary"
## 
## $no.children
## [1] 3
## 
## $child.ages
## [1] 4 7 9
{% endhighlight %}

{% highlight s %}
myL[[4]][1:2] 
{% endhighlight %}

{% highlight s %}
## [1] 4 7
{% endhighlight %}

__Functions__: piece of code


{% highlight s %}
myfct <- function(arg1, arg2, ...) { 
	function_body 
}
{% endhighlight %}

## Subsetting of data objects

__Subsetting by positive or negative index/position numbers__


{% highlight s %}
myVec <- 1:26; names(myVec) <- LETTERS 
myVec[1:4]
{% endhighlight %}

{% highlight s %}
## A B C D 
## 1 2 3 4
{% endhighlight %}

__Subsetting by same length logical vectors__


{% highlight s %}
myLog <- myVec > 10
myVec[myLog] 
{% endhighlight %}

{% highlight s %}
##  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  Y  Z 
## 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26
{% endhighlight %}

__Subsetting by field names__


{% highlight s %}
myVec[c("B", "K", "M")]
{% endhighlight %}

{% highlight s %}
##  B  K  M 
##  2 11 13
{% endhighlight %}

__Subset with `$` sign__: references a single column or list component by its name 


{% highlight s %}
iris$Species[1:8]
{% endhighlight %}

{% highlight s %}
## [1] setosa setosa setosa setosa setosa setosa setosa setosa
## Levels: setosa versicolor virginica
{% endhighlight %}

Plotting example

{% highlight s %}
barplot(1:10, col="green")
{% endhighlight %}

![](images/vignette_Rbasics/plot_example-1.png)\



{% highlight sh %}
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
## [1] ggplot2_2.0.0   limma_3.26.3    BiocStyle_1.8.0
## 
## loaded via a namespace (and not attached):
##  [1] Rcpp_0.12.3      codetools_0.2-14 digest_0.6.9     plyr_1.8.3       grid_3.2.3      
##  [6] gtable_0.1.2     formatR_1.2.1    magrittr_1.5     evaluate_0.8     scales_0.3.0    
## [11] stringi_1.0-1    rmarkdown_0.9.2  tools_3.2.3      stringr_1.0.0    munsell_0.4.2   
## [16] yaml_2.1.13      colorspace_1.2-6 htmltools_0.3    knitr_1.12
{% endhighlight %}



