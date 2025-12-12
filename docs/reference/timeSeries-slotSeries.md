# Get and set the data component of a 'timeSeries'

Get and set the data component of a 'timeSeries'.

## Usage

``` r
series(x)
series(x) <- value
```

## Arguments

- x:

  a `timeSeries` object.

- value:

  a `vector`, a `data.frame` or a `matrix` object of numeric data.

## Details

`series` returns the `@.Data` slot of a `timeSeries` object in `matrix`
form.

The assignment version of `series` replaces the values of the time
series with `value`. The row and column names of `value` are used if not
`NULL`, otherwise they are left as in `x`. The most natural use is when
`value` has the same dimensions as `as.matrix(x)`, but if that is not
the case the result is almost as if `value` was converted to
`"timeSeries"` directly.

Methods for [`zoo::coredata`](https://rdrr.io/pkg/zoo/man/coredata.html)
and its assignment counterpart are defined, as well. Users who wish to
use them should ensure that
[`zoo::coredata`](https://rdrr.io/pkg/zoo/man/coredata.html) is visible
(e.g., by calling [`library('zoo')`](https://zoo.R-Forge.R-project.org/)
or [`library('xts')`](https://joshuaulrich.github.io/xts/)) or employ
the `zoo::` prefix in the calls. These methods are equivalent to
`series` and `` `series<-` ``, respectively.

## See also

[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md)

## Examples

``` r
## A Dummy 'timeSeries' Object
   ts <- timeSeries()
   ts
#>  
#>      SS.1
#> [1,]   NA

## Get the Matrix Part - 
   mat <- series(ts)
   class(mat)
#> [1] "matrix" "array" 
   mat
#>      SS.1
#> [1,]   NA

## Assign a New Univariate Series - 
   series(ts) <- rnorm(12)
   ts
#>  
#>             SS.1
#>  [1,]  0.5747557
#>  [2,] -1.0236557
#>  [3,] -0.0151383
#>  [4,] -0.9359486
#>  [5,]  1.1022975
#>  [6,] -0.4755931
#>  [7,] -0.7094400
#>  [8,] -0.5012581
#>  [9,] -1.6290935
#> [10,] -1.1676193
#> [11,] -2.1800396
#> [12,] -1.3409932
   
## Assign a New Bivariate Series - 
   series(ts) <- matrix(rnorm(12), ncol = 2)
   ts
#>  
#>            SS.1       SS.2
#> [1,] -0.2942939 -0.9943401
#> [2,] -0.4658975 -0.9685143
#> [3,]  1.4494963 -1.1073182
#> [4,] -1.0686427 -1.2519859
#> [5,] -0.8553646 -0.5238281
#> [6,] -0.2806230 -0.4968500
```
