# Apply functions over time windows

Applies a function to a `"timeSeries"` object over regular or irregular
time windows, possibly overlapping.

## Usage

``` r
# S4 method for class 'timeSeries'
apply(X, MARGIN, FUN, ..., simplify = TRUE)

fapply(x, from, to, FUN, ...)

applySeries(x, from = NULL, to = NULL, by = c("monthly", "quarterly"), 
            FUN = colMeans, units = NULL, format = x@format, 
            zone = x@FinCenter, FinCenter = x@FinCenter, 
            recordIDs = data.frame(), title = x@title, 
            documentation = x@documentation, ...)

rollDailySeries(x, period = "7d", FUN, ...)
```

## Arguments

- x,X:

  an object of class `timeSeries`.

- MARGIN:

  a vector giving the subscripts which the function will be applied
  over, see base R's [`apply`](https://rdrr.io/r/base/apply.html).

- FUN:

  the function to be applied. For the function `applySeries` the default
  setting is `FUN = colMeans`.

- simplify:

  simplify the result?

- from, to:

  starting date and end date as `"timeDate"` objects. Note, `to` must be
  time ordered after `from`. If `from` and `to` are missing in function
  `fapply` they are set by default to `from=start(x)`, and `to=end(x)`.

- by:

  a character value either `"monthly"` or `"quarterly"` used in the
  function `applySeries`. The default value is `"monthly"`. Only
  operative when both arguments `from` and `to` have their default
  values `NULL`. In this case the function `FUN` will be applied to
  monthly or quarterly periods.

- units:

  an optional character string, which allows to overwrite the current
  column names of a `timeSeries` object. By default `NULL` which means
  that the column names are selected automatically.

- format:

  the format specification of the input character vector in POSIX
  notation.

- zone:

  the time zone or financial center where the data were recorded.

- FinCenter:

  a character value with the the location of the financial center named
  as "continent/city", or "city".

- recordIDs:

  a data frame which can be used for record identification information.
  Note, this is not yet handled by the apply functions, an empty
  data.frame will be returned.

- title:

  an optional title string, if not specified the input's data name is
  deparsed.

- documentation:

  optional documentation string, or a vector of character strings.

- period:

  a character string specifying the rollling period composed by the
  length of the period and its unit, e.g. `"7d"` represents one week.

- ...:

  arguments passed to other methods.

## Details

The `"timeSeries"` method for `apply` extracts the core data (a matrix)
from `X` and calls `apply`, passing on all the remaining arguments. If
the result is suitable, it converts it to `"timeSeries"`, otherwise
returns it as is. ‘Suitable’ here means that it is a matrix or a vector
(which is converted to a matrix) and the number of observations is the
same as `X`.

Like `apply` applies a function to the margins of an array, the function
`fapply` applies a function to the time stamps or signal counts of a
financial (therefore the “f” in front of the function name) time series
of class `"timeSeries"`.

`applySeries` takes a `"timeSeries"` object as input and applies `FUN`
to windows of `x`. The windows are specified by `from` and `to`, which
need to have the same length. Then `from[i], to[i]` specifies the `i`-th
window. If `time(x)` is a `"timeDate"` object, then `from` and `to` are
converted to `"timeDate"` (if they are not already such objects),
otherwise they are converted to integers.

An alternative way to specify the window(s) on which `applySeries`
operates is with argument `by`. It is used only if `from` and `to` are
missing or `NULL`. `by = "monthly"` or `by = "quarterly"` applies `FUN`
to the data for each year-month or year-quarter, respectively. By
year-month we mean that there are separate windows for the months in
different years.

The resulting time stamps are the time stamps of the `to` vector. The
periods can be regular or irregular, and they can even overlap.

If `from = start(x)` and `to = end(x)`, then the function behaves like
`apply` on the column margin.

`fapply` is the same as `applySeries` (in fact, the former calls the
latter), except that the defaults for `from` and `to` are `start(x)` and
`end(x)`, respectively. (GNB: in addition, `fapply` throws error if `x`
is a ‘signal series’.)

`rollDailySeries` rolls a daily 'timeSeries' on a given period.

## Value

for `rollDailySeries`, an object of class `"timeSeries"` with rolling
values, computed from the function `FUN`.

## Examples

``` r
## Percentual Returns of Swiss Bond Index and Performance Index - 
   LPP <- 100 * LPP2005REC[, c("SBI", "SPI")]
   head(LPP, 20)
#> GMT 
#>                   SBI        SPI
#> 2005-11-01 -0.0612745  0.8414595
#> 2005-11-02 -0.2762009  0.2519342
#> 2005-11-03 -0.1153092  1.2707292
#> 2005-11-04 -0.3235750 -0.0702757
#> 2005-11-07  0.1310970  0.6205226
#> 2005-11-08  0.0539312  0.0329260
#> 2005-11-09 -0.2545021 -0.2378200
#> 2005-11-10  0.1003358  0.0922087
#> 2005-11-11  0.0616951  1.3334906
#> 2005-11-14  0.0693615 -0.4693064
#> 2005-11-15  0.0154071  0.1266865
#> 2005-11-16  0.2999656 -0.7187498
#> 2005-11-17 -0.1306436  0.7658103
#> 2005-11-18 -0.2232573  1.2527202
#> 2005-11-21  0.1155402  0.2659666
#> 2005-11-22 -0.0230974  0.2142494
#> 2005-11-23  0.0692761  0.3567128
#> 2005-11-24  0.2075407 -0.2559544
#> 2005-11-25 -0.0614487  0.3374818
#> 2005-11-28 -0.0307385 -0.9816739
   
## Aggregate Quarterly Returns -
   applySeries(LPP, by = "quarterly", FUN = colSums)
#> GMT 
#>                   SBI       SPI
#> 2005-12-31  0.5193189  7.295300
#> 2006-03-31 -1.6590275  7.074801
#> 2006-06-30 -1.1685058 -3.428832
#> 2006-09-30  2.7589662  9.780371
#> 2006-12-31 -0.0076177  5.359906
#> 2007-03-31 -0.2595182  3.604943
#> 2007-06-30 -0.1682858  2.047652
   
## Aggregate Quarterly every last Friday in Quarter -
   oneDay <- 24*3600
   from <- unique(timeFirstDayInQuarter(time(LPP))) - oneDay
   from <- timeLastNdayInMonth(from, nday = 5)
   to <- unique(timeLastDayInQuarter(time(LPP)))
   to <- timeLastNdayInMonth(to, nday = 5)
   data.frame(from = as.character(from), to = as.character(to))
#>         from         to
#> 1 2005-09-30 2005-12-30
#> 2 2005-12-30 2006-03-31
#> 3 2006-03-31 2006-06-30
#> 4 2006-06-30 2006-09-29
#> 5 2006-09-29 2006-12-29
#> 6 2006-12-29 2007-03-30
#> 7 2007-03-30 2007-06-29

   applySeries(LPP, from, to, FUN = colSums)
#> GMT 
#>                   SBI       SPI
#> 2005-12-30  0.5193189  7.295300
#> 2006-03-31 -1.7047209  6.677154
#> 2006-06-30 -1.1452689 -3.521758
#> 2006-09-29  2.7041309 11.227752
#> 2006-12-29 -0.1295039  5.500849
#> 2007-03-30 -0.1451061  3.494746
#> 2007-06-29 -0.1988528  2.097361
## Alternative Use - 
   fapply(LPP, from, to, FUN = colSums)
#> GMT 
#>                   SBI       SPI
#> 2005-12-30  0.5193189  7.295300
#> 2006-03-31 -1.7047209  6.677154
#> 2006-06-30 -1.1452689 -3.521758
#> 2006-09-29  2.7041309 11.227752
#> 2006-12-29 -0.1295039  5.500849
#> 2007-03-30 -0.1451061  3.494746
#> 2007-06-29 -0.1988528  2.097361
   
## Count Trading Days per Month - 
   colCounts <- function(x) rep(NROW(x), times = NCOL(x))
   applySeries(LPP, FUN = colCounts, by = "monthly")
#> GMT 
#>            SBI SPI
#> 2005-11-30  22  22
#> 2005-12-31  22  22
#> 2006-01-31  22  22
#> 2006-02-28  20  20
#> 2006-03-31  23  23
#> 2006-04-30  20  20
#> 2006-05-31  23  23
#> 2006-06-30  22  22
#> 2006-07-31  21  21
#> 2006-08-31  23  23
#> 2006-09-30  21  21
#> 2006-10-31  22  22
#> 2006-11-30  22  22
#> 2006-12-31  21  21
#> 2007-01-31  23  23
#> 2007-02-28  20  20
#> 2007-03-31  22  22
#> 2007-04-30   8   8


## TODO: examples for rollDailySeries()
```
