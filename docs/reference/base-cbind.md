# Bind 'timeSeries' objects by column or row

Binds `"timeSeries"` objects either by column or by row.

## Usage

``` r
# S3 method for class 'timeSeries'
cbind(..., deparse.level = 1)
# S3 method for class 'timeSeries'
rbind(..., deparse.level = 1)

# S4 method for class 'timeSeries,ANY'
cbind2(x, y)
## other methods for 'cbind2' with the same arguments, see Details

# S4 method for class 'timeSeries,ANY'
rbind2(x, y)
## other methods for 'rbind2' with the same arguments, see Details
```

## Arguments

- x, y:

  objects, at least one of whom is of class `"timeSeries"`.

- ...:

  further arguments to bind.

- deparse.level:

  see the documentation of
  [`base::cbind`](https://rdrr.io/r/base/cbind.html).

## Details

These functions bind the objects by row `rXXX` or column (`cXXX`.

`cbind` and `rbind` are S3 generics, so the `"timeSeries"` methods
describe here are called only when the first argument is `"timeSeries"`.

`cbind2` and `rbind2` are S4 generics which dispatch on the first two
arguments. The `"timeSeries"` methods for these are invoked whenever at
least one of the first two arguments is of class `"timeSeries"`.

All functions can be called with more than two arguments. After the
first two are merged, the result is merged with the third, and so on.

## Value

an object of class `"timeSeries"`

## See also

[`merge`](https://geobosh.github.io/timeSeriesDoc/reference/base-merge.md)
for another way to merge `"timeSeries"` object column-wise.

[`rbind`](https://rdrr.io/r/base/cbind.html) and
[`cbind`](https://rdrr.io/r/base/cbind.html) from base R,

[`rbind2`](https://rdrr.io/r/methods/cbind2.html) and
[`cbind2`](https://rdrr.io/r/methods/cbind2.html) from package
`"methods"`,

## Examples

``` r
## Load Microsoft Data Set -
   x <- MSFT[1:12, ]
   x
#> GMT 
#>               Open    High     Low   Close   Volume
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250 53077800
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125 26180200
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125 37026800
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250 29281200
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625 42687000
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375 68226700
#> 2000-10-05 55.5000 57.2500 55.2500 55.3750 40549700
#> 2000-10-06 55.8125 56.7500 54.7500 55.5625 30897000
#> 2000-10-09 55.6250 55.7500 53.0000 54.1875 29161800
#> 2000-10-10 53.9375 55.5625 53.8125 54.5625 31033100
#> 2000-10-11 54.0000 56.9375 54.0000 55.7500 50602900
#> 2000-10-12 56.3125 56.8750 53.8125 54.3750 45109800

## Bind Columnwise -
   X <- cbind(x[, "Open"], returns(x[, "Open"]))
   colnames(X) <- c("Open", "Return")
   X
#> GMT 
#>               Open       Return
#> 2000-09-27 63.4375           NA
#> 2000-09-28 60.8125 -0.042259809
#> 2000-09-29 61.0000  0.003078504
#> 2000-10-02 60.5000 -0.008230499
#> 2000-10-03 59.5625 -0.015617184
#> 2000-10-04 56.3750 -0.055000384
#> 2000-10-05 55.5000 -0.015642777
#> 2000-10-06 55.8125  0.005614838
#> 2000-10-09 55.6250 -0.003365118
#> 2000-10-10 53.9375 -0.030806772
#> 2000-10-11 54.0000  0.001158078
#> 2000-10-12 56.3125  0.041932489

## Bind Rowwise - 
   Y <- rbind(x[1:3, "Open"], x[10:12, "Open"])
   Y
#> GMT 
#>            Open_Open
#> 2000-09-27   63.4375
#> 2000-09-28   60.8125
#> 2000-09-29   61.0000
#> 2000-10-10   53.9375
#> 2000-10-11   54.0000
#> 2000-10-12   56.3125
```
