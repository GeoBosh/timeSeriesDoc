# Cumulated column statistics

Functions to compute cumulative column statistics.

## Usage

``` r
# S4 method for class 'timeSeries'
colCumsums(x, na.rm = FALSE, ...)

# S4 method for class 'timeSeries'
colCummaxs(x, na.rm = FALSE, ...)

# S4 method for class 'timeSeries'
colCummins(x, na.rm = FALSE, ...)

# S4 method for class 'timeSeries'
colCumprods(x, na.rm = FALSE, ...)

# S4 method for class 'timeSeries'
colCumreturns(x, method = c("geometric", "simple"),
                                     na.rm = FALSE, ...)
```

## Arguments

- x:

  a time series, may be an object of class `"matrix"`, or
  `"timeSeries"`.

- na.rm:

  a logical. Should missing values be removed?

- method:

  a character string to indicate if geometric (`TRUE`) or simple
  (`FALSE`) returns should be computed.

- ...:

  arguments to be passed.

## Details

These functions compute the requested cumulative quantities columnwise
to obtain a matrix of the same dimension as the data. The `"timeSeries"`
methods replace the data part of the original object with the resulting
matrix.

The `"timeSeries"` methods for the `Math` group functions `cummin`,
`cummax`, `cumsum`, and `cumprod`, work similarly but don't have the
`na.rm` argument.

## Value

`"matrix"` for the default methods of all functions,

`"timeSeries"` for the `"timeSeries"` methods

## See also

[`Math,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md),
[`rowCumsums`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rowCumsums.md)

## Examples

``` r
## simulate return data
x <- matrix(rnorm(24), ncol = 2)
X <- as.timeSeries(x)
     
## cumulative sums  by column  -
class(colCumsums(x))  # "matrix"
#> [1] "matrix" "array" 
class(colCumsums(X))  # "timeSeries"
#> [1] "timeSeries"
#> attr(,"package")
#> [1] "timeSeries"

colCumsums(X)
#>  
#>              SS.1       SS.2
#>  [1,] -0.46904286 -0.6683035
#>  [2,] -0.08946295  0.2142997
#>  [3,] -0.62408849  0.4325942
#>  [4,]  0.40762881  2.1981422
#>  [5,]  1.11719544  3.3405613
#>  [6,]  1.19564445  2.7493640
#>  [7,]  2.17172488  2.1315335
#>  [8,]  1.90963785  1.3705165
#>  [9,]  0.53934139  1.0829842
#> [10,]  0.73558623 -1.4763901
#> [11,] -0.47676941 -3.3161513
#> [12,] -0.63562514 -1.6435476
```
