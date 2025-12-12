# Durations from a 'timeSeries'

Computes durations from an object of class `"timeSeries"`.

## Usage

``` r
durations(x, trim = FALSE, units = c("secs", "mins", "hours", "days"))
```

## Arguments

- x:

  an object of class `"timeSeries"`.

- trim:

  a logical value. By default `TRUE`, the first missing observation in
  the return series will be removed.

- units:

  a character value or vector which allows to set the units in which the
  durations are measured. By default durations are measured in seconds.

## Details

Durations measure how long it takes until we get the next record in a
`timesSeries` object. We return a time series in which for each time
stamp we get the length of the period from when we got the last record.
This period is measured in length specified by the argument `units`, for
daily data use `units="days"`.

## Value

an object of class `"timeSeries"`

## Examples

``` r
## Compute Durations in days for the MSFT Sereries - 
   head(durations(MSFT, units = "days"))
#> GMT 
#>            Duration
#> 2000-09-27       NA
#> 2000-09-28        1
#> 2000-09-29        1
#> 2000-10-02        3
#> 2000-10-03        1
#> 2000-10-04        1
   head(durations(MSFT, trim = TRUE, units = "days"))
#> GMT 
#>            Duration
#> 2000-09-28        1
#> 2000-09-29        1
#> 2000-10-02        3
#> 2000-10-03        1
#> 2000-10-04        1
#> 2000-10-05        1

## The same in hours - 
   head(durations(MSFT, trim = TRUE, units = "hours"))
#> GMT 
#>            Duration
#> 2000-09-28       24
#> 2000-09-29       24
#> 2000-10-02       72
#> 2000-10-03       24
#> 2000-10-04       24
#> 2000-10-05       24
```
