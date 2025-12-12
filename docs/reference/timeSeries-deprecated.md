# Deprecated functions in 'timeSeries' package

`seriesData` (removed) extracts data slot from a 'timeSeries'. use
[`as.matrix`](https://rdrr.io/r/base/matrix.html) instead.

## Usage

``` r
removeNA(x, ...)
```

## Arguments

- x:

  a numeric matrix, or any other object which can be transformed into a
  matrix through `x = as.matrix(x, ...)`. If `x` is a vector, it will be
  transformed into a one-dimensional matrix.

- ...:

  arguments to be passed to the function `as.matrix`.
