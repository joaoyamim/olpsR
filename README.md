---
title: "OLPS"
author: "ngloe"
date: "17.03.2015"
output: html_document
bibliography: OLPS.bib
---
The OLPS package provides different On-line Portfolio Selection algorithms
and functions to deal with the on-line portfolio selection problem where a portfolio is rebalanced in every period to achieve certain goals, e.g. maximizing terminal wealth. For a background on On-line Portfolio Selection see for example [@LH14; <http://arxiv.org/pdf/1212.2129.pdf>]. Datasets to test portfolio selection algorithms are also included. 

## On-Line Portfolio Selection algorithms:
* Buy-and-Hold
* Buy-and-Hold best
* Constant Rebalanced Portfolio
* Best Constant Rebalanced Portfolio
* Universal Portfolio [@Cov91]
* Exponential Gradient [@HSS98]
* ...

## Functions
* transform asset prices into returns (price relatuives)
* transform returns (price relatuives) into asset prices
* calculate portfolio wealth of rebalanced portfolios
* transform a sequence of price relatives into a Kelly market sequence
* ...

## Datasets
* NYSE dataset [used by @Cov91, @HSS98, ...]
* DAX dataset


# Installation
To install the OLPS package run

```r
if (!require("devtools")) install.packages("devtools")
devtools::install_github("ngloe/OLPS")
```

# Getting started
Once installed, the package can be loaded in a given R session using:

```r
library(OLPS)
```

To test portfolio selection algorithms some return data is loaded using the NYSE dataset. We select two assets, *kinar* and *iroqu*:

```r
data(NYSE)
x <- cbind(kinar=NYSE$kinar, iroqu=NYSE$iroqu)
```

Algorithms can be run by applying *calc_ALG* on the selected data where *ALG* is the desired algorithm. For example, to calculate the Best Constant Rebalanced Portfolio (BCRP) type:


```r
BCRP <- calc_BCRP(x)
BCRP
```

```
## SUMMARY of BCRP :
## 
## Assets                kinar iroqu 
## 
## Terminal Wealth       73.70091 
## expected log-Return   0.1901988 
## expected Risk         0.477619 
## Return-to-Risk        0.3982229
```
Accessing BCRP then returns a short summary of the algorithm's output. To access the calculated portfolio wealth or the portfolio weights you can type:

```r
BCRPS$Wealth
BCRPS$Weights
```
The achieved portfolio wealth (performance) can be plotted by

```r
plot(BCRP)
```

![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7-1.png) 

# References
