# Spreads and mid quotes

Compute spreads and midquotes from price streams.

## Usage

``` r
spreads(x, which = c("Bid", "Ask"), tickSize = NULL)    
midquotes(x, which = c("Bid", "Ask"))
```

## Arguments

- x:

  an object of class `timeSeries`.

- which:

  a vector with two character strings naming the column names of the
  time series from which to compute the mid quotes and spreads. By
  default these are the bid and ask prices with column names
  `c("Bid", "Ask")`.

- tickSize:

  the default is `NULL` to simply compute price changes in original
  price levels. If `ticksize` is supplied, the price changes will be
  divided by the value of `inTicksOfSize` to compute price changes in
  ticks.

## Value

all functions return an object of class `timeSeries`

## See also

[`returns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md),
[`cumulated`](https://geobosh.github.io/timeSeriesDoc/reference/fin-cumulated.md),
[`drawdowns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md),
[`splits`](https://geobosh.github.io/timeSeriesDoc/reference/fin-splits.md),
`midquotes`,
[`index2wealth`](https://geobosh.github.io/timeSeriesDoc/reference/fin-wealth.md)

## Examples

``` r
## Load the Microsoft Data -  
   setRmetricsOptions(myFinCenter = "GMT")
   data(MSFT)
   X = MSFT[1:10, ]
   head(X)
#> GMT 
#>               Open    High     Low   Close   Volume
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250 53077800
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125 26180200
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125 37026800
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250 29281200
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625 42687000
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375 68226700

## Compute Open/Close Midquotes -
   X.MID <- midquotes(X, which = c("Close", "Open"))
   colnames(X.MID) <- "X.MID"
   X.MID
#> GMT 
#>               X.MID
#> 2000-09-27 62.03125
#> 2000-09-28 61.06250
#> 2000-09-29 60.65625
#> 2000-10-02 59.81250
#> 2000-10-03 58.06250
#> 2000-10-04 55.90625
#> 2000-10-05 55.43750
#> 2000-10-06 55.68750
#> 2000-10-09 54.90625
#> 2000-10-10 54.25000

## Compute Open/Close Spreads -
   X.SPREAD <- spreads(X, which = c("Close", "Open"))
   colnames(X.SPREAD) <- "X.SPREAD"
   X.SPREAD
#> GMT 
#>            X.SPREAD
#> 2000-09-27   2.8125
#> 2000-09-28  -0.5000
#> 2000-09-29   0.6875
#> 2000-10-02   1.3750
#> 2000-10-03   3.0000
#> 2000-10-04   0.9375
#> 2000-10-05   0.1250
#> 2000-10-06   0.2500
#> 2000-10-09   1.4375
#> 2000-10-10  -0.6250
```
