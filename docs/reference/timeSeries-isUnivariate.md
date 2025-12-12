# Checks if a time series is univariate

Checks if a time series object or any other rectangular object is
univariate or multivariate.

## Usage

``` r
isUnivariate(x)
isMultivariate(x)
```

## Arguments

- x:

  an object of class `"timeSeries"` or any other rectangular object.

## Details

A rectangular object `x` is considered to be univariate if the function
`NCOL(x)` returns one, and is considered to be multivariate if `NCOL(x)`
returns a value bigger than one.

## Value

a logical value

## Examples

``` r
## Load Microsoft Data - 
   setRmetricsOptions(myFinCenter = "GMT")
   data(MSFT)
   Open = MSFT[, "Open"]
  
## Is the 'timeSeries' Univariate - 
   isUnivariate(MSFT)
#> [1] FALSE
   isUnivariate(Open)
#> [1] TRUE

## Is the 'timeSeries' Multivariate -   
   isMultivariate(MSFT)
#> [1] TRUE
   isMultivariate(Open)
#> [1] FALSE
```
