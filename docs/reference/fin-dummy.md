# Create dummy time series

Create dummy daily and monthly time series for examples and exploration.

## Usage

``` r
dummyDailySeries(x = rnorm(365), units = NULL, zone = "", 
                 FinCenter = "")

dummyMonthlySeries(...)
```

## Arguments

- x:

  an object of class `timeSeries`.

- units:

  an optional character string, which allows to overwrite the current
  column names of a `timeSeries` object. By default `NULL` which means
  that the column names are selected automatically.

- FinCenter:

  a character with the the location of the financial center named as
  `"continent/city"`.

- zone:

  the time zone or financial center where the data were recorded.

- ...:

  optional arguments passed to `timeSeries`.

## Details

`dummyDailySeries` creates a `timeSeries` object with dummy daily dates
from a numeric matrix with daily records of unknown dates.

`dummyMonthlySeries` creates a dummy monthly `"timeSeries"` object.

## Value

a `"timeSeries"` object

## Examples

``` r
dd <- dummyDailySeries()
head(dd)
#> GMT 
#>                     X1
#> 1970-01-01 -0.53462554
#> 1970-01-02  1.03171730
#> 1970-01-03  0.70956662
#> 1970-01-04  0.07844901
#> 1970-01-05  0.97608044
#> 1970-01-06 -0.26208703
tail(dd)
#> GMT 
#>                    X1
#> 1970-12-26 -0.6550923
#> 1970-12-27  0.9025630
#> 1970-12-28 -0.5051588
#> 1970-12-29  1.4303289
#> 1970-12-30 -2.8277936
#> 1970-12-31  0.8543979

dummyMonthlySeries(y = 2022)
#> GMT 
#>                 TS.1       TS.2
#> 2025-01-01 0.8121176 0.57928300
#> 2025-02-01 0.9931157 0.73721491
#> 2025-03-01 0.1822492 0.81422727
#> 2025-04-01 0.8045545 0.02083266
#> 2025-05-01 0.5473774 0.60258179
#> 2025-06-01 0.5935642 0.58940310
#> 2025-07-01 0.3782178 0.35845328
#> 2025-08-01 0.2984592 0.51053485
#> 2025-09-01 0.5675508 0.11299805
#> 2025-10-01 0.2742155 0.80668108
#> 2025-11-01 0.7835054 0.21732771
#> 2025-12-01 0.5305348 0.40583530
```
