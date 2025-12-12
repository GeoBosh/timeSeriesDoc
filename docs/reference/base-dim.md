# Dimension and their names for 'timeSeries' objects

Get and assign names, row names, column names, and dim names of
`"timeSeries"` objects.

## Details

`"timeSeries"` methods are available for base R functions working on
dimension names, including `dim`, `dimnames`, `colnames`, `rownames`,
`names` and their assignment variants.

`dim` is the dimension of the underlying data matrix.

`rownames` gives the datetime stamps as a character vector. `rownames<-`
sets them.

`colnames` gives the values of `x@units`. These are conceptually the
column names of the data matrix. `colnames<-` sets slot `units` of `x`.

`dimnames` gives `list(rownames(x), colnames(x)`. `dimnames<-` calls
`rownames` and `colnames` on `value[[1]]` and `value[[2]]`,
respectively.

## Note

(GNB; todo) The `"dim<-"`, currently converts `x` to a vector if `value`
is `NULL`, otherwise it ignores `value`, does nothing and returns `x`
unchanged. This behaviour should not be relied upon and may be changed
in the future, e.g. by issuing warning when `value` is not `NULL`. Or
throwing error altogether if assignment with `"dim<-"` is attempted.

## Examples

``` r
## Load Swiss Pension Fund Benchmark Data -
   X <- LPP2005REC[1:10, 1:3]
   
## Get Dimension - 
   dim(X)
#> [1] 10  3
   
## Get Column and Row Names -
   dimnames(X)
#> [[1]]
#>  [1] "2005-11-01" "2005-11-02" "2005-11-03" "2005-11-04" "2005-11-07"
#>  [6] "2005-11-08" "2005-11-09" "2005-11-10" "2005-11-11" "2005-11-14"
#> 
#> [[2]]
#> [1] "SBI" "SPI" "SII"
#> 
   
## Get Column / Row Names -
   colnames(X)
#> [1] "SBI" "SPI" "SII"
   rownames(X) 
#>  [1] "2005-11-01" "2005-11-02" "2005-11-03" "2005-11-04" "2005-11-07"
#>  [6] "2005-11-08" "2005-11-09" "2005-11-10" "2005-11-11" "2005-11-14"
   
## Try your own DIM - 
   DIM <- function(x) {c(NROW(x), NCOL(x))}
   DIM(X) 
#> [1] 10  3
   DIM(X[, 1])
#> [1] 10  1

## Try length / LENGTH - 
   length(X)
#> [1] 30
   length(X[, 1])
#> [1] 10
   LENGTH <- function(X) NROW(X)
   LENGTH(X)
#> [1] 10
   
## Columns / Rows - 
   ncol(X); NCOL(X)
#> [1] 3
#> [1] 3
   nrow(X); NROW(X)
#> [1] 10
#> [1] 10
                
## See also - 
   isUnivariate(X)
#> [1] FALSE
   isMultivariate(X)
#> [1] TRUE
```
