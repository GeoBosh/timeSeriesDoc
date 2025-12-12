# Align a 'timeSeries' object to equidistant time stamps

Aligns a `"timeSeries"` object to equidistant time stamps. There are
also functions for the common cases of changing daily to weekly and
daily to monthly.

## Usage

``` r
# S4 method for class 'timeSeries'
align(x, by = "1d", offset = "0s",
    method = c("before", "after", "interp", "fillNA",
               "fmm", "periodic", "natural", "monoH.FC"),
    include.weekends = FALSE, ...)

alignDailySeries(x, method = c("before", "after", "interp", "fillNA",
    "fmm", "periodic", "natural", "monoH.FC"),
    include.weekends = FALSE, units = NULL, zone = "",
    FinCenter = "", ...)

daily2monthly(x, init = FALSE) 
daily2weekly(x, startOn = "Tue", init = FALSE)
```

## Arguments

- x:

  an object of class `"timeSeries"`.

- by:

  a character string denoting the period.

- offset:

  a character string denoting the offset.

- method:

  the method to be used for the alignment. A character string, one of
  `"before"`, use the data from the row whose position is just before
  the unmatched position, or `"after"`, use the data from the row whose
  position is just after the unmatched position, or `"linear"`,
  interpolate linearly between `"before"` and `"after"`.

- include.weekends:

  a logical value. Should weekend dates be included or removed from the
  series?

- units:

  an optional character string, which allows to overwrite the current
  column names of a `timeSeries` object. By default `NULL` which means
  that the column names are selected automatically.

- zone:

  the time zone or financial center where the data were recorded.

- FinCenter:

  a character with the the location of the financial center named as
  `"continent/city"`.

- startOn:

  a character string, specifying the day of week as a three letter
  abbreviation. Weekly aggregated data records are then fixed to the
  weekdays given by the argument `startOn`.

- init:

  a logical value, if set to `TRUE` then the time series will be indexed
  to 1 for its first value. By default `init` is set to `FALSE`.

- ...:

  further arguments to be passed to the interpolating function.

## Details

TODO: complete.

`alignDailySeries` aligns a daily 'timeSeries' to new positions,
Effectively, it is a frontend to the `"timeSeries"` method for `align`
with `by = "1d"`, and `offset = "0s"`.

In addition, there are two tailored functions for common cases:
`daily2monthly` and `daily2weekly` which aggregate `"timeSeries"`
objects from daily to monthly or weekly levels, respectively.

In the case of the function `daily2weekly` one can explicitly set the
starting day of the week, the default value is Tuesday,
`startOn = "Tue"`.

## See also

[`aggregate`](https://geobosh.github.io/timeSeriesDoc/reference/stats-aggregate.md),
[`apply`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)

## Value

a `"timeSeries"` object,

for `alignDailySeries`, a weekly aligned daily `"timeSeries"` object
from a daily time series with missing holidays.

## Examples

``` r
## Use Microsofts' OHLCV Price Series -
   head(MSFT)
#> GMT 
#>               Open    High     Low   Close   Volume
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250 53077800
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125 26180200
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125 37026800
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250 29281200
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625 42687000
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375 68226700
   end(MSFT)
#> GMT
#> [1] [2001-09-27]

## Use MSFT and Compute Sample Size -
   dim(MSFT)
#> [1] 249   5

## Align the Series -
   MSFT.AL <- align(MSFT)

## Show the Size of the Aligned Series -
   dim(MSFT.AL)
#> [1] 262   5


## alignDailySeries

## Cut out April Data from 2001 -
   Close <- MSFT[, "Close"]
   tsApril01 <- window(Close, start="2001-04-01", end="2001-04-30")
   tsApril01
#> GMT 
#>              Close
#> 2001-04-02 55.8125
#> 2001-04-03 53.3750
#> 2001-04-04 51.9375
#> 2001-04-05 56.7500
#> 2001-04-06 56.1875
#> 2001-04-09 57.1500
#> 2001-04-10 59.6800
#> 2001-04-11 60.0400
#> 2001-04-12 62.1800
#> 2001-04-16 60.7900
#> 2001-04-17 61.4800
#> 2001-04-18 65.4300
#> 2001-04-19 68.0400
#> 2001-04-20 69.0000
#> 2001-04-23 68.2500
#> 2001-04-24 67.5500
#> 2001-04-25 69.6900
#> 2001-04-26 69.1300
#> 2001-04-27 67.1200
#> 2001-04-30 67.7500

## Align Daily Series with NA -
   tsRet <- returns(tsApril01, trim = TRUE)
   GoodFriday(2001)
#> GMT
#> [1] [2001-04-13]
   EasterMonday(2001)
#> GMT
#> [1] [2001-04-16]
   alignDailySeries(tsRet, method = "fillNA", include.weekends = FALSE)
#> GMT 
#>                   Close
#> 2001-04-03 -0.044655387
#> 2001-04-04 -0.027301399
#> 2001-04-05  0.088614584
#> 2001-04-06 -0.009961344
#> 2001-04-09  0.016985078
#> 2001-04-10  0.043317566
#> 2001-04-11  0.006014051
#> 2001-04-12  0.035022398
#> 2001-04-13           NA
#> 2001-04-16 -0.022608103
#> 2001-04-17  0.011286617
#> 2001-04-18  0.062268950
#> 2001-04-19  0.039114899
#> 2001-04-20  0.014010737
#> 2001-04-23 -0.010929071
#> 2001-04-24 -0.010309370
#> 2001-04-25  0.031188771
#> 2001-04-26 -0.008068045
#> 2001-04-27 -0.029506728
#> 2001-04-30  0.009342398
   alignDailySeries(tsRet, method = "fillNA", include.weekends = TRUE)
#> GMT 
#>                   Close
#> 2001-04-03 -0.044655387
#> 2001-04-04 -0.027301399
#> 2001-04-05  0.088614584
#> 2001-04-06 -0.009961344
#> 2001-04-07           NA
#> 2001-04-08           NA
#> 2001-04-09  0.016985078
#> 2001-04-10  0.043317566
#> 2001-04-11  0.006014051
#> 2001-04-12  0.035022398
#> 2001-04-13           NA
#> 2001-04-14           NA
#> 2001-04-15           NA
#> 2001-04-16 -0.022608103
#> 2001-04-17  0.011286617
#> 2001-04-18  0.062268950
#> 2001-04-19  0.039114899
#> 2001-04-20  0.014010737
#> 2001-04-21           NA
#> 2001-04-22           NA
#> 2001-04-23 -0.010929071
#> 2001-04-24 -0.010309370
#> 2001-04-25  0.031188771
#> 2001-04-26 -0.008068045
#> 2001-04-27 -0.029506728
#> 2001-04-28           NA
#> 2001-04-29           NA
#> 2001-04-30  0.009342398

## Align Daily Series by Interpolated Values -
   alignDailySeries(tsRet, method = "interp", include.weekend = FALSE)
#> GMT 
#>                   Close
#> 2001-04-03 -0.044655387
#> 2001-04-04 -0.027301399
#> 2001-04-05  0.088614584
#> 2001-04-06 -0.009961344
#> 2001-04-09  0.016985078
#> 2001-04-10  0.043317566
#> 2001-04-11  0.006014051
#> 2001-04-12  0.035022398
#> 2001-04-13  0.020614773
#> 2001-04-16 -0.022608103
#> 2001-04-17  0.011286617
#> 2001-04-18  0.062268950
#> 2001-04-19  0.039114899
#> 2001-04-20  0.014010737
#> 2001-04-23 -0.010929071
#> 2001-04-24 -0.010309370
#> 2001-04-25  0.031188771
#> 2001-04-26 -0.008068045
#> 2001-04-27 -0.029506728
#> 2001-04-30  0.009342398
   alignDailySeries(tsRet, method = "interp", include.weekend = TRUE)
#> GMT 
#>                    Close
#> 2001-04-03 -0.0446553871
#> 2001-04-04 -0.0273013989
#> 2001-04-05  0.0886145837
#> 2001-04-06 -0.0099613441
#> 2001-04-07 -0.0009792034
#> 2001-04-08  0.0080029373
#> 2001-04-09  0.0169850780
#> 2001-04-10  0.0433175657
#> 2001-04-11  0.0060140509
#> 2001-04-12  0.0350223979
#> 2001-04-13  0.0206147727
#> 2001-04-14  0.0062071475
#> 2001-04-15 -0.0082004777
#> 2001-04-16 -0.0226081029
#> 2001-04-17  0.0112866169
#> 2001-04-18  0.0622689502
#> 2001-04-19  0.0391148986
#> 2001-04-20  0.0140107371
#> 2001-04-21  0.0056974679
#> 2001-04-22 -0.0026158013
#> 2001-04-23 -0.0109290705
#> 2001-04-24 -0.0103093697
#> 2001-04-25  0.0311887710
#> 2001-04-26 -0.0080680455
#> 2001-04-27 -0.0295067278
#> 2001-04-28 -0.0165570193
#> 2001-04-29 -0.0036073109
#> 2001-04-30  0.0093423976


## Load Microsoft Data Set -
   x <- MSFT

## Aggregate daily records to end of month records -
   X <- daily2monthly(x)
   X
#> GMT 
#>               Open    High     Low   Close   Volume
#> 2000-09-30 61.0000 61.3125 58.6250 60.3125 37026800
#> 2000-10-31 69.0000 69.5000 68.0000 68.8750 52237000
#> 2000-11-30 62.0000 62.0625 57.0000 57.3750 98600400
#> 2000-12-31 43.9375 45.8125 43.0000 43.3750 49988800
#> 2001-01-31 63.0000 63.7500 61.0000 61.0625 40949400
#> 2001-02-28 59.5625 60.0781 58.1875 59.0000 42304200
#> 2001-03-31 55.7500 56.1875 53.8750 54.6875 45600800
#> 2001-04-30 68.5300 69.0600 67.6800 67.7500 37184100
#> 2001-05-31 69.4900 70.3800 68.4000 69.1800 35341300
#> 2001-06-30 72.6000 73.4100 71.4000 73.0000 47141900
#> 2001-07-31 66.0100 67.3900 65.8500 66.1900 29515800
#> 2001-08-31 56.8500 58.0600 56.3000 57.0500 28950400
#> 2001-09-30 50.1000 50.6800 48.0000 49.9600 40595600
   isMonthly(X)
#> [1] TRUE
   
## Aggregate daily records to end of week records -
   X <- daily2weekly(x, startOn="Fri")
   X
#> GMT 
#>               Open    High     Low   Close    Volume
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125  37026800
#> 2000-10-06 55.8125 56.7500 54.7500 55.5625  30897000
#> 2000-10-13 53.8750 54.8750 52.1250 53.7500  52260600
#> 2000-10-20 61.3125 66.1250 61.1250 65.1875  80189300
#> 2000-10-27 64.6875 69.1875 64.6250 67.6875  62146200
#> 2000-11-03 69.2500 69.6250 68.0625 68.2500  34355500
#> 2000-11-10 69.9375 70.3125 66.8125 67.3750  46872200
#> 2000-11-17 69.4375 70.0000 67.7969 69.0625  53262800
#> 2000-11-24 69.0000 70.4375 68.5000 69.9375  17219600
#> 2000-12-01 58.0625 60.6250 56.0625 56.6250  54904900
#> 2000-12-08 54.6250 55.8750 53.4375 54.4375  60469900
#> 2000-12-15 51.0469 52.0000 47.7500 49.1875  58449900
#> 2000-12-22 44.7500 47.1250 44.7500 46.4375  54775900
#> 2000-12-29 43.9375 45.8125 43.0000 43.3750  49988800
#> 2001-01-05 48.5000 49.8750 47.5625 49.1250  46707300
#> 2001-01-12 54.8750 55.0000 52.5000 53.5000  36856000
#> 2001-01-19 60.0000 61.4375 58.8750 61.0000 104674400
#> 2001-01-26 61.0000 64.3125 61.0000 64.0000  46540000
#> 2001-02-02 62.5000 63.3750 60.7500 60.8125  35550000
#> 2001-02-09 61.3125 61.5625 58.5000 59.1250  50287600
#> 2001-02-16 57.0000 58.2500 56.1250 57.3125  33479200
#> 2001-02-23 54.4375 57.5000 54.3125 56.7500  46310300
#> 2001-03-02 57.5000 58.1250 56.4375 56.6875  39900400
#> 2001-03-09 57.9375 58.1875 54.8750 56.6875  51897200
#> 2001-03-16 52.5000 55.1250 52.4844 54.5625  56424400
#> 2001-03-23 54.9375 57.0000 54.3750 56.5625  49759800
#> 2001-03-30 55.7500 56.1875 53.8750 54.6875  45600800
#> 2001-04-06 56.3750 57.1875 55.0625 56.1875  46311000
#> 2001-04-13 59.5600 62.3100 59.3500 62.1800  43760000
#> 2001-04-20 70.3000 71.1000 68.5000 69.0000  96459800
#> 2001-04-27 69.5300 69.6800 66.2100 67.1200  60786200
#> 2001-05-04 68.0000 71.0500 67.9600 70.7500  59769200
#> 2001-05-11 69.9600 70.0000 68.6500 69.4000  25564400
#> 2001-05-18 67.6900 69.2000 67.2500 68.0900  45302700
#> 2001-05-25 71.6600 71.9000 70.3600 70.9100  26373800
#> 2001-06-01 69.6000 70.7000 68.7000 70.3400  28793800
#> 2001-06-08 73.7000 73.7500 72.0500 73.1900  25933500
#> 2001-06-15 67.5100 68.3000 66.4000 68.0200  54177200
#> 2001-06-22 70.0000 70.6100 68.5800 68.8300  25546000
#> 2001-06-29 72.6000 73.4100 71.4000 73.0000  47141900
#> 2001-07-06 68.3000 68.4000 65.6700 66.0600  33733900
#> 2001-07-13 71.4000 72.0000 70.9400 71.3400  29467300
#> 2001-07-20 68.0300 69.4000 67.9400 69.1800  62101800
#> 2001-07-27 66.0500 66.2500 65.0500 65.4700  32698000
#> 2001-08-03 67.3000 67.3600 66.0000 66.8900  21630200
#> 2001-08-10 64.7700 65.8600 62.9000 65.5200  25878200
#> 2001-08-17 63.7800 64.1300 61.5000 61.8800  26117100
#> 2001-08-24 59.6000 62.2800 59.2300 62.0500  31699500
#> 2001-08-31 56.8500 58.0600 56.3000 57.0500  28950400
#> 2001-09-07 56.1100 57.3600 55.3100 55.4000  44931900
#> 2001-09-14 54.9200 57.9500 54.7000 57.5800  42235900
#> 2001-09-21 47.9200 50.6000 47.5000 49.7100  92488300
   dayOfWeek(time(X))
#> 2000-09-29 2000-10-06 2000-10-13 2000-10-20 2000-10-27 2000-11-03 2000-11-10 
#>      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri" 
#> 2000-11-17 2000-11-24 2000-12-01 2000-12-08 2000-12-15 2000-12-22 2000-12-29 
#>      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri" 
#> 2001-01-05 2001-01-12 2001-01-19 2001-01-26 2001-02-02 2001-02-09 2001-02-16 
#>      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri" 
#> 2001-02-23 2001-03-02 2001-03-09 2001-03-16 2001-03-23 2001-03-30 2001-04-06 
#>      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri" 
#> 2001-04-13 2001-04-20 2001-04-27 2001-05-04 2001-05-11 2001-05-18 2001-05-25 
#>      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri" 
#> 2001-06-01 2001-06-08 2001-06-15 2001-06-22 2001-06-29 2001-07-06 2001-07-13 
#>      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri" 
#> 2001-07-20 2001-07-27 2001-08-03 2001-08-10 2001-08-17 2001-08-24 2001-08-31 
#>      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri"      "Fri" 
#> 2001-09-07 2001-09-14 2001-09-21 
#>      "Fri"      "Fri"      "Fri" 
```
