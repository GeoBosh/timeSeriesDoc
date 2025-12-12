# Order statistics

Computes the order statistics of a `"timeSeries"` object.

## Usage

``` r
orderStatistics(x)
```

## Arguments

- x:

  a `"timeSeries"` object.

## Details

`orderStatistics` computes the order statistics for each column of a
`"timeSeries"` object. The output is a named list with the order
statistics for each column in a separate component.

## Value

a named list, in which each component is an univariate `"timeSeries"`
containing the order statistics of the corresponding column of the input
time series.

## Examples

``` r
## Load Swiss Pension Fund Benchmark Data -  
   setRmetricsOptions(myFinCenter = "GMT")
   X <- LPP2005REC[, "SPI"]
   colnames(X)
#> [1] "SPI"
   
## Compute 1% Order Statistics -
   N <- round(0.01*nrow(X))
   N
#> [1] 4
   OS <- orderStatistics(X)[[1]]
   OS[1:N, ]
#> GMT 
#>                    SPI
#> 2007-02-27 -0.03574624
#> 2006-05-17 -0.02840692
#> 2007-03-14 -0.02820549
#> 2006-06-08 -0.02737931
```
