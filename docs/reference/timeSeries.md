# Create objects from class 'timeSeries'

`timeSeries` creates a `"timeSeries"` object from scratch.

## Usage

``` r
timeSeries(data, charvec, units = NULL, format = NULL, zone = "", 
           FinCenter = "", recordIDs = data.frame(), title = NULL, 
           documentation = NULL, ...)
```

## Arguments

- data:

  a `matrix` object or any objects which can be coerced to a matrix.

- charvec:

  a character vector of dates and times or any objects which can be
  coerced to a `"timeDate"` object.

- units:

  an optional character string, which allows to overwrite the current
  column names of a `"timeSeries"` object. By default `NULL` which means
  that the column names are selected automatically.

- format:

  the format specification of the input character vector, a character
  string with the format in POSIX notation.

- zone:

  the time zone or financial center where the data were recorded.

- FinCenter:

  a character with the the location of the financial center named as
  "continent/city".

- recordIDs:

  for `timeSeries`, a data frame which can be used for record
  identification.

- title:

  an optional title string, if not specified the input's data name is
  deparsed.

- documentation:

  optional documentation string, or a vector of character strings.

- ...:

  arguments passed to other methods.

## Value

an S4 object of class `"timeSeries"`

## Details

**Generation of Time Series Objects:**  

We have defined a `"timeSeries"` class which is in many aspects similar
to the S-Plus class with the same name, but has also some important
differences. The class has seven Slots, the 'Data' slot which holds the
time series data in matrix form, the 'position' slot which holds the
time/date as a character vector, the 'format' and 'FinCenter' slots
which are the same as for the 'timeDate' object, the 'units' slot which
holds the column names of the data matrix, and a 'title' and a
'documentation' slot which hold descriptive character strings. Date and
time is managed in the same way as for `timeDate` objects.

[`as.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
also creates `"timeSeries"` objects. `as.timeSeries(x)` is mostly
equivalent to `timeSeries(x)` but the two functions have different
methods. Beside that, the main difference between the two functions is
that `as.timeSeries` doesn't accept additional arguments. The one
argument call is naturally interpreted as ‘convert to’, so
[`as.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
is more expressive and is recommended in that case.

`"timeSeries"` methods are provided for many base R functions, including
arithmetic operations, mathematical functions, `print`, `summary`, and
time series functions. Not all are explicitly documented, since they can
just be used.

## See also

[`as.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md),
class
[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-class.md),

## Examples

``` r
## Load Microsoft data -
   # Microsoft Data: 
   setRmetricsOptions(myFinCenter = "GMT")
   data(MSFT)
   head(MSFT)
#> GMT 
#>               Open    High     Low   Close   Volume
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250 53077800
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125 26180200
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125 37026800
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250 29281200
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625 42687000
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375 68226700

## Create a 'timeSeries' object, the direct Way ...
   Close <- MSFT[, 5]
   head(Close)
#> GMT 
#>              Volume
#> 2000-09-27 53077800
#> 2000-09-28 26180200
#> 2000-09-29 37026800
#> 2000-10-02 29281200
#> 2000-10-03 42687000
#> 2000-10-04 68226700
   
## Create a 'timeSeries' object from scratch - 
   data <- as.matrix(MSFT[, 4])
   charvec <- rownames(MSFT)
   Close <- timeSeries(data, charvec, units = "Close")
   head(Close)
#> GMT 
#>              Close
#> 2000-09-27 60.6250
#> 2000-09-28 61.3125
#> 2000-09-29 60.3125
#> 2000-10-02 59.1250
#> 2000-10-03 56.5625
#> 2000-10-04 55.4375
   c(start(Close), end(Close))
#> GMT
#> [1] [2000-09-27] [2001-09-27]

## Cut out April data from 2001 - 
   tsApril01 <- window(Close, "2001-04-01", "2001-04-30") 
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

## Compute Continuous Returns - 
   returns(tsApril01)
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
   
## Compute Discrete Returns - 
   returns(tsApril01, type = "discrete")
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
   
## Compute Discrete Returns, Don't trim -
   returns(tsApril01, trim = FALSE)
#> GMT 
#>                   Close
#> 2001-04-02           NA
#> 2001-04-03 -0.044655387
#> 2001-04-04 -0.027301399
#> 2001-04-05  0.088614584
#> 2001-04-06 -0.009961344
#> 2001-04-09  0.016985078
#> 2001-04-10  0.043317566
#> 2001-04-11  0.006014051
#> 2001-04-12  0.035022398
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
   
## Compute Discrete Returns, Use Percentage Values - 
   tsRet <- returns(tsApril01, percentage = TRUE, trim = FALSE)
   tsRet
#> GMT 
#>                 Close
#> 2001-04-02         NA
#> 2001-04-03 -4.4655387
#> 2001-04-04 -2.7301399
#> 2001-04-05  8.8614584
#> 2001-04-06 -0.9961344
#> 2001-04-09  1.6985078
#> 2001-04-10  4.3317566
#> 2001-04-11  0.6014051
#> 2001-04-12  3.5022398
#> 2001-04-16 -2.2608103
#> 2001-04-17  1.1286617
#> 2001-04-18  6.2268950
#> 2001-04-19  3.9114899
#> 2001-04-20  1.4010737
#> 2001-04-23 -1.0929071
#> 2001-04-24 -1.0309370
#> 2001-04-25  3.1188771
#> 2001-04-26 -0.8068045
#> 2001-04-27 -2.9506728
#> 2001-04-30  0.9342398
     
## Aggregate Weekly - 
   GoodFriday(2001)
#> GMT
#> [1] [2001-04-13]
   to <- timeSequence(from = "2001-04-11", length.out = 3, by = "week") 
   from <- to - 6*24*3600
   from
#> GMT
#> [1] [2001-04-05] [2001-04-12] [2001-04-19]
   to
#> GMT
#> [1] [2001-04-11] [2001-04-18] [2001-04-25]
   applySeries(tsRet, from, to, FUN = sum)
#> GMT 
#>                Close
#> 2001-04-11 14.496993
#> 2001-04-18  8.596986
#> 2001-04-25  6.307597

## Create large 'timeSeries' objects with different 'charvec' object classes - 
   # charvec is a 'timeDate' object
   head(timeSeries(1:1e6L, timeSequence(length.out = 1e6L, by = "sec")))
#> GMT 
#>                     TS.1
#> 2025-11-13 16:28:28    1
#> 2025-11-13 16:28:29    2
#> 2025-11-13 16:28:30    3
#> 2025-11-13 16:28:31    4
#> 2025-11-13 16:28:32    5
#> 2025-11-13 16:28:33    6
   head(timeSeries(1:1e6L, seq(Sys.timeDate(), length.out = 1e6L, by = "sec")))
#> GMT 
#>                     TS.1
#> 2025-12-12 16:28:28    1
#> 2025-12-12 16:28:29    2
#> 2025-12-12 16:28:30    3
#> 2025-12-12 16:28:31    4
#> 2025-12-12 16:28:32    5
#> 2025-12-12 16:28:33    6
   # 'charvec' is a 'POSIXt' object
   head(timeSeries(1:1e6L, seq(Sys.time(), length.out = 1e6L, by = "sec")))
#> GMT 
#>                     TS.1
#> 2025-12-12 16:28:28    1
#> 2025-12-12 16:28:29    2
#> 2025-12-12 16:28:30    3
#> 2025-12-12 16:28:31    4
#> 2025-12-12 16:28:32    5
#> 2025-12-12 16:28:33    6
   # 'charvec' is a 'numeric' object
   head(timeSeries(1:1e6L, 1:1e6L))
#> GMT 
#>                     TS.1
#> 1970-01-01 00:00:01    1
#> 1970-01-01 00:00:02    2
#> 1970-01-01 00:00:03    3
#> 1970-01-01 00:00:04    4
#> 1970-01-01 00:00:05    5
#> 1970-01-01 00:00:06    6
```
