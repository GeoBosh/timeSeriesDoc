# Checks if a time series is regular

Checks if a time series is regular.

## Usage

``` r
# S4 method for class 'timeSeries'
isDaily(x)
# S4 method for class 'timeSeries'
isMonthly(x)
# S4 method for class 'timeSeries'
isQuarterly(x)

# S4 method for class 'timeSeries'
isRegular(x)

# S4 method for class 'timeSeries'
frequency(x, ...)
```

## Arguments

- x:

  an R object of class 'timeSeries'.

- ...:

  arguments to be passed.

## Details

What is a regular time series? If a time series is daily, monthly, or
weekly, then we speak of a regular series. This can be tested calling
the functions `isDaily`, `isMonthly`, `isQuarterly`, or in general
`isRegular`. If the series is regular then its frequency can be
determined by calling `frequency`.

Here are the definitions of daily, monthly, and quarterly time series:

- daily:

  if the series has no more than one date/time stamp per day.

- monthly:

  if the series has no more than one date/time stamp per month.

- quarterly:

  if the series has no more than one date/time stamp per quarter.

A regular series is either a monthly or a quarterly series.

Note that with the above definitions a monthly series is also a daily
series, a quarterly series is also a monthly series. On the other hand,
a daily series is not regular!

NOT yet implemented is the case of weekly series.

## Value

The `is*` functions return `TRUE` or `FALSE` depending on whether the
series fulfills the condition or not.  

`frequency` returns in general 1, for quarterly series 4, and for
monthly series 12.

## See also

[`isRegular`](https://geobosh.github.io/timeDateDoc/reference/calendar-isRegular.html)
[`frequency`](https://rdrr.io/r/stats/time.html)

## Examples

``` r
data(MSFT)
isRegular(MSFT) # FALSE
#> [1] FALSE
frequency(MSFT) # 1
#> [1] 1

## a monthly ts
ap <- as.timeSeries(AirPassengers)
isRegular(ap) # TRUE
#> [1] TRUE
frequency(ap) # 12
#> [1] 12

## a quarterly ts
pres <- as.timeSeries(presidents)
isRegular(pres) # TRUE
#> [1] TRUE
frequency(pres) # 4
#> [1] 4
```
