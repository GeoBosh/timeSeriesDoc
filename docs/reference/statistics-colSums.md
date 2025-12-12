# Column statistics

A collection of functions to compute column statistical properties of
financial and economic time series data.

## Usage

``` r
colStats(x, FUN, ...) 

colSds(x, ...)
colVars(x, ...)
colSkewness(x, ...)
colKurtosis(x, ...)
colMaxs(x, ...)
colMins(x, ...)
colProds(x, ...)
colQuantiles(x, prob = 0.05, ...)
```

## Arguments

- x:

  a rectangular object which can be transformed into a matrix by the
  function `as.matrix`.

- FUN:

  a function name, the statistical function to be applied.

- prob:

  a numeric value in \[0,1\].

- ...:

  arguments to be passed.

## Details

|                |                                                |
|----------------|------------------------------------------------|
| `colStats`     | calculates column statistics,                  |
| `colSums`      | calculates column sums,                        |
| `colMeans`     | calculates column means,                       |
| `colSds`       | calculates column standard deviations,         |
| `colVars`      | calculates column variances,                   |
| `colSkewness`  | calculates column skewness,                    |
| `colKurtosis`  | calculates column kurtosis,                    |
| `colMaxs`      | calculates maximum values in each column,      |
| `colMins`      | calculates minimum values in each column,      |
| `colProds`     | computes product of all values in each column, |
| `colQuantiles` | computes quantiles of each column.             |

## Value

each function returns a numeric vector of the statistics, one for each
column

## See also

[`rollStats`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)

## Examples

``` r
## Simulated Return Data in Matrix Form -
   x = matrix(rnorm(252), ncol = 2)
     
## Mean Columnwise Statistics -
   colStats(x, FUN = mean)
#> [1] -0.03156255 -0.05679949
   
## Quantiles Column by Column -
   colQuantiles(x, prob = 0.10, type = 1)  
#> [1] -1.289635 -1.272006
```
