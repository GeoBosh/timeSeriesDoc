# Base R functions applied to 'timeSeries' objects

Many base R statistical functions work on (the data part of)
`timeSeries` objects without the need for special methods, e.g., `var`,
`sd`, `cov`, `cor`, probability densities, and others. This page gives
some examples with such functions.

## See also

[`colStats`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md),
[`colVars`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md),
and other `colXXX` functions

## Examples

``` r
## Load Microsoft Data Set - 
   data(MSFT)
   X = MSFT[, 1:4]
   X = 100 * returns(X)

## Compute Covariance Matrix - 
   cov(X[, "Open"], X[, "Close"])
#>         Close
#> Open 5.370449
   cov(X)
#>            Open     High       Low     Close
#> Open  12.024989 7.717341  9.072359  5.370449
#> High   7.717341 8.566159  8.007279  7.931451
#> Low    9.072359 8.007279 10.543072  8.505720
#> Close  5.370449 7.931451  8.505720 11.676740

cor(X)   
#>            Open      High       Low     Close
#> Open  1.0000000 0.7603828 0.8057388 0.4532183
#> High  0.7603828 1.0000000 0.8425745 0.7930467
#> Low   0.8057388 0.8425745 1.0000000 0.7665963
#> Close 0.4532183 0.7930467 0.7665963 1.0000000
```
