# Sample ranks of a time series

Compute the sample ranks of the values of a 'timeSeries' object.

## Usage

``` r
# S4 method for class 'timeSeries'
rank(x, na.last = TRUE, ties.method = )
```

## Arguments

- x:

  an univariate object of class `timeSeries`.

- na.last:

  for controlling the treatment of `NA`s. If `TRUE`, missing values in
  the data are put last; if `FALSE`, they are put first; if `NA`, they
  are removed; if `"keep"` they are kept with rank `NA`.

- ties.method:

  a character string specifying how ties are treated; can be
  abbreviated.

## Details

If all components are different (and no `NA`s), the ranks are well
defined, with values in `seq_len(x)`. With some values equal (called
‘ties’), argument `ties.method` determines the result at the
corresponding indices. The `"first"` method results a permutation with
increasing values at each index set of ties. The `"random"` method puts
these in random order, whereas the default, `"average"`, replaces them
by their mean, and `"max"` and `"min"` replace them with their maximum
and minimum respectively, the latter being the typical sports ranking.

`NA` values are never considered to be equal: for `na.last = TRUE` and
`na.last = FALSE` they are given distinct ranks in the order in which
they occur in `x`.

## Value

a `"timeSeries"` object

## Examples

``` r
## Load Microsoft Data -
   X <- 100 * returns(MSFT)

## Compute the Ranks -
   head(rank(X[, "Open"]), 10)
#> GMT 
#>            Open
#> 2000-09-28   18
#> 2000-09-29  138
#> 2000-10-02  107
#> 2000-10-03   87
#> 2000-10-04    8
#> 2000-10-05   86
#> 2000-10-06  147
#> 2000-10-09  122
#> 2000-10-10   44
#> 2000-10-11  132
   
## Only Interested in the Vector, then use -
   head(rank(series(X[, "Open"])), 10)
#>  [1]  18 138 107  87   8  86 147 122  44 132
```
