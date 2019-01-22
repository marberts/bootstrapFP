
<!-- README.md is generated from README.Rmd. Please edit that file -->
bootstrapFP
===========

[![Travis-CI Build Status](https://travis-ci.org/rhobis/bootstrapFP.svg?branch=master)](https://travis-ci.org/rhobis/bootstrapFP) [![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/bootstrapFP)](https://cran.r-project.org/package=bootstrapFP) [![](https://cranlogs.r-pkg.org/badges/grand-total/bootstrapFP)](https://cran.r-project.org/package=bootstrapFP)

Description
-----------

This package provides bootstrap algorithms for Finite Population inference, for estimating the variance of the Horvitz--Thompson estimator.

Installation
------------

To install the package from CRAN, run the following code in *R*:

``` r
install.packages("bootstrapFP")
```

Or, for the development version:

``` r
# if not present, install 'devtools' package
install.packages("devtools")
devtools::install_github("rhobis/bootstrapFP")
```

Usage
-----

``` r
library(bootstrapFP) 

### Generate population data ---
N   <- 20; n <- 5
x   <- rgamma(N, scale=10, shape=5)
y   <- abs( 2*x + 3.7*sqrt(x) * rnorm(N) )
pik <- n * x/sum(x)

### Draw a dummy sample ---
s  <- sample(N, n)

### Estimate bootstrap variance ---
bootstrapFP(y = y[s], pik = n/N, B=100, method = "ppSitter")
bootstrapFP(y = y[s], pik = pik[s], B=10, method = "ppHolmberg", design = 'brewer')
bootstrapFP(y = y[s], pik = pik[s], B=10, D=10, method = "ppChauvet")
bootstrapFP(y = y[s], pik = pik[s], B=10, method = "wGeneralised", distribution = 'normal')
bootstrapFP(y = y[s], pik = n/N, B=10, method = "dRaoWu")
bootstrapFP(y = y[s], pik = n/N, B=10, method = "dSitter")
bootstrapFP(y = y[s], pik = pik[s], B=10, method = "dAntalTille_UPS", design='brewer')
bootstrapFP(y = y[s], pik = n/N, B=10, method = "wRaoWuYue") 
bootstrapFP(y = y[s], pik = n/N, B=10, method = "wChipperfieldPreston")
```

More
----

-   Please, report any bug or issue [here](https://github.com/rhobis/bootstrapFP/issues).
-   For more information, please contact the maintainer at `roberto.sichera@unipa.it`.
