# Special monthly series

Functions and methods dealing with special monthly `"timeSeries"`
objects.

## Usage

``` r
rollMonthlyWindows(x, period = "12m", by = "1m") 

rollMonthlySeries(x, period = "12m", by = "1m", FUN, ...)
countMonthlyRecords(x)
```

## Arguments

- x:

  a `"timeSeries"` object.

- period,by:

  character strings specifying the rollling period composed by the
  length of the period and its unit. Examples: `"3m"`, `"6m"`, `"12m"`,
  and `"24m"` represent quarterly, semi-annual, annual and bi-annual
  shifts, respectively. It is the responsibility of the user to
  determine proper start of the series.

- FUN:

  the function for the statistic to be applied. For example, `colMean`
  in the case of aggregation.

- ...:

  arguments passed to the function `FUN`.

## Details

`rollMonthlySeries` computes the statistics defined by the function
`FUN` over rolling windows, internally computed by the function
`rollMonthlyWindows`. Note, the periods may be overlapping, may be
dense, or even may have gaps.

`countMonthlyRecords` computes a `"timeSeries"` that holds the number of
records for each month, see examples. The dates are set to the end of
the month.

`rollMonthlyWindows` computes start and end dates for rolling time
windows. Argument `period` specifies the length of the periods over
which `FUN` is applied, while `by` gives the amount by which the window
is shifted. Non-overlapping windows correspond to `by >= period`.

## Value

for `countMonthlyRecords` and `rollMonthlySeries`, a `"timeSeries"`
object.

for `rollMonthlyWindows`, a list with attribute `"control"` keeping the
`start` and `end` dates of the series. The components of the list are:

- from:

  an object from class `"timeDate"`.

- to:

  an object from class `"timeDate"`.

## See also

[`isMonthly`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md),
[`isRegular`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)

## Examples

``` r
## load Microsoft daily dataset
x <- MSFT 

## count monthly records
head(x)   # 3 obs. for Sep 2000
#> GMT 
#>               Open    High     Low   Close   Volume
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250 53077800
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125 26180200
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125 37026800
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250 29281200
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625 42687000
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375 68226700
counts <- countMonthlyRecords(x)
counts
#> GMT 
#>            Counts
#> 2000-09-30      3
#> 2000-10-31     22
#> 2000-11-30     21
#> 2000-12-31     20
#> 2001-01-31     21
#> 2001-02-28     19
#> 2001-03-31     22
#> 2001-04-30     20
#> 2001-05-31     22
#> 2001-06-30     21
#> 2001-07-31     21
#> 2001-08-31     23

## diy computation of the counts
diy <- rollMonthlySeries(x[ , 1], period = "1m", by = "1m", FUN = NROW)

## difference is only in some attributes (e.g. column names)
all.equal(diy,  counts)
#> [1] "Names: 1 string mismatch"                                            
#> [2] "Attributes: < Component “dimnames”: Component 2: 1 string mismatch >"
#> [3] "Attributes: < Component “units”: 1 string mismatch >"                

   
## quaterly non-overlapping time periods
windows <- rollMonthlyWindows(counts[-1, ], period = "3m", by = "3m") 
windows
#> $from
#> GMT
#> [1] [2000-10-01] [2000-11-01] [2000-12-01] [2001-01-01] [2001-02-01]
#> [6] [2001-03-01] [2001-04-01] [2001-05-01]
#> 
#> $to
#> GMT
#> [1] [2000-12-31] [2001-01-31] [2001-02-28] [2001-03-31] [2001-04-30]
#> [6] [2001-05-31] [2001-06-30] [2001-07-31]
#> 
#> attr(,"control")
#> GMT
#>        start          end 
#> [2000-10-31] [2001-08-31] 
## nicely print results as a data.frame, each row is a time window
data.frame(cbind(FROM = format(windows$from), TO = format(windows$to)))
#>         FROM         TO
#> 1 2000-10-01 2000-12-31
#> 2 2000-11-01 2001-01-31
#> 3 2000-12-01 2001-02-28
#> 4 2001-01-01 2001-03-31
#> 5 2001-02-01 2001-04-30
#> 6 2001-03-01 2001-05-31
#> 7 2001-04-01 2001-06-30
#> 8 2001-05-01 2001-07-31
   
## compute the average number of monthly trading days per quarter
rollMonthlySeries(counts[-1, ], period = "3m", by = "3m", FUN = mean)
#> GMT 
#>              Counts
#> 2000-12-31 21.00000
#> 2001-01-31 20.66667
#> 2001-02-28 20.00000
#> 2001-03-31 20.66667
#> 2001-04-30 20.33333
#> 2001-05-31 21.33333
#> 2001-06-30 21.00000
#> 2001-07-31 21.33333
```
