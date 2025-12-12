# Check if an object is from class 'timeSeries'

`is.timeSeries` tests if its argument is a `timeSeries`.
`is.signalSeries` tests if series has no timestamps.

## Usage

``` r
is.timeSeries(x)
is.signalSeries(x)
```

## Arguments

- x:

  an object.

## Value

a logical value, `TRUE` or `FALSE`.

## Examples

``` r
## Create an artificial 'timeSeries' object - 
   setRmetricsOptions(myFinCenter = "GMT")
   charvec <- timeCalendar()
   data <- matrix(rnorm(12))
   TS <- timeSeries(data, charvec, units = "RAND")
   TS
#> GMT 
#>                    RAND
#> 2025-01-01 -2.559374272
#> 2025-02-01 -1.839761220
#> 2025-03-01  1.672603722
#> 2025-04-01 -1.272653368
#> 2025-05-01  0.001369812
#> 2025-06-01 -0.231584632
#> 2025-07-01 -1.947726847
#> 2025-08-01  0.602454282
#> 2025-09-01  0.742540487
#> 2025-10-01  0.234180532
#> 2025-11-01  1.949510250
#> 2025-12-01  0.819855589

## Test for 'timeSeries' - 
   is.timeSeries(TS)
#> [1] TRUE
```
