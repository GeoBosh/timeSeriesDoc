# Cumulative row statistics

Compute cumulative row statistics.

## Usage

``` r
# S4 method for class 'ANY'
rowCumsums(x, na.rm = FALSE, ...)
# S4 method for class 'timeSeries'
rowCumsums(x, na.rm = FALSE, ...)
```

## Arguments

- x:

  a time series, may be an object of class `"matrix"` or `"timeSeries"`.

- na.rm:

  a logical. Should missing values be removed?

- ...:

  arguments to be passed.

## Value

for the default method, a matrix,

for the `"timeSeries"` method, an S4 object of class `"timeSeries"`.

## See also

[`colCumXXX`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)

## Examples

``` r
## Simulated Monthly Return Data - 
   X = matrix(rnorm(24), ncol = 2)
     
## Compute cumulated Sums -
   rowCumsums(X)  
#>             [,1]       [,2]
#>  [1,] -1.4156946 -1.8622381
#>  [2,] -0.2790816  0.6510722
#>  [3,] -0.7343694 -1.1184703
#>  [4,] -2.3219978 -1.3368371
#>  [5,]  0.2352241  0.7688533
#>  [6,]  1.0409608 -0.2712446
#>  [7,]  0.1788792  1.1847917
#>  [8,]  1.1806609  0.6898419
#>  [9,]  0.4943278  0.6654160
#> [10,]  0.2950635  0.6313672
#> [11,]  1.1047098  2.5060845
#> [12,] -1.8764122 -0.7874266
```
