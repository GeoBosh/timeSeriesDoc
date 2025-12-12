# Lag a 'timeSeries' object

Compute a lagged version of a `"timeSeries"` object.

## Usage

``` r
# S3 method for class 'timeSeries'
lag(x, k = 1, trim = FALSE, units = NULL, ...)
```

## Arguments

- x:

  an object of class `timeSeries`.

- k:

  an integer number, the number of lags (in units of observations). By
  default 1. Can also be a vector, in which case the result is a
  multivariate `"timeSeries"` in which column `i` contains the series
  lagged by `k[i]`, see the examples.

- trim:

  a logical value. By default `TRUE`, the first missing observation in
  the return series will be removed.

- units:

  an optional character string, which allows to overwrite the current
  column names of a `"timeSeries"` object. By default `NULL` which means
  that the column names are selected automatically.

- ...:

  arguments passed to other methods.

## Value

an object of class `"timeSeries"`

## See also

[`lag`](https://rdrr.io/r/stats/lag.html) for `stats::lag`,
[`diff`](https://geobosh.github.io/timeSeriesDoc/reference/base-diff.md)

## Examples

``` r
## Load Micsrosoft Data Set
x <- MSFT[1:20, "Open"]
   
## Lag the 'timeSeries' Object
lag(x, k = -1:1)
#> GMT 
#>            Open[-1] Open[0] Open[1]
#> 2000-09-27  60.8125 63.4375      NA
#> 2000-09-28  61.0000 60.8125 63.4375
#> 2000-09-29  60.5000 61.0000 60.8125
#> 2000-10-02  59.5625 60.5000 61.0000
#> 2000-10-03  56.3750 59.5625 60.5000
#> 2000-10-04  55.5000 56.3750 59.5625
#> 2000-10-05  55.8125 55.5000 56.3750
#> 2000-10-06  55.6250 55.8125 55.5000
#> 2000-10-09  53.9375 55.6250 55.8125
#> 2000-10-10  54.0000 53.9375 55.6250
#> 2000-10-11  56.3125 54.0000 53.9375
#> 2000-10-12  53.8750 56.3125 54.0000
#> 2000-10-13  53.5000 53.8750 56.3125
#> 2000-10-16  51.8750 53.5000 53.8750
#> 2000-10-17  49.6250 51.8750 53.5000
#> 2000-10-18  58.4375 49.6250 51.8750
#> 2000-10-19  61.3125 58.4375 49.6250
#> 2000-10-20  64.6250 61.3125 58.4375
#> 2000-10-23  62.6250 64.6250 61.3125
#> 2000-10-24       NA 62.6250 64.6250
```
