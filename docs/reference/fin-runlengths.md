# Runlengths of a time series

Computes runlengths of an univariate `"timeSeries"` object.

## Usage

``` r
runlengths(x, ...)
```

## Arguments

- x:

  an univariate time series of class `"timeSeries"`.

- ...:

  arguments passed to the function `na.omit`.

## Details

Runlengths are defined here as contiguous sequences of values having the
same sign.

Zeroes are treated as `NA`s.

## Value

an object of class `"timeSeries"`

## Examples

``` r
## random time series - 
   set.seed(4711)
   x <- rnorm(12)
   tS <- timeSeries(data = x, charvec = timeCalendar(), units = "x")
   tS
#> GMT 
#>                      x
#> 2025-01-01  1.81973511
#> 2025-02-01  1.37043950
#> 2025-03-01  1.19631824
#> 2025-04-01 -0.40687920
#> 2025-05-01 -0.61097880
#> 2025-06-01 -1.50891205
#> 2025-07-01  0.81754941
#> 2025-08-01 -0.96466789
#> 2025-09-01 -0.04452208
#> 2025-10-01  0.47435474
#> 2025-11-01 -0.98216632
#> 2025-12-01 -1.57211053
   
## return runlengths -
   runlengths(tS)
#> GMT 
#>            x
#> 2025-03-01 3
#> 2025-06-01 3
#> 2025-07-01 1
#> 2025-09-01 2
#> 2025-10-01 1
#> 2025-12-01 2

## replace the middle value of the negative stretch of 3 values
tS[5] <- NA
## the two negative values separated by NA are still one run
runlengths(tS)
#> GMT 
#>            x
#> 2025-03-01 3
#> 2025-05-01 2
#> 2025-06-01 1
#> 2025-08-01 2
#> 2025-09-01 1
#> 2025-11-01 2
```
