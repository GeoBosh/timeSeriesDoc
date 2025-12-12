# Conversion of an index to wealth

Converts an index series to a wealth series normalizing the starting
value to one.

## Usage

``` r
index2wealth(x)
```

## Arguments

- x:

  an object of class 'timeSeries'.

## Value

returns a time series object of the same class as the input argument `x`
normalizing the starting value to one.

## See also

[`returns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md),
[`cumulated`](https://geobosh.github.io/timeSeriesDoc/reference/fin-cumulated.md),
[`drawdowns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md),
[`splits`](https://geobosh.github.io/timeSeriesDoc/reference/fin-splits.md),
[`spreads`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md),
[`midquotes`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md),

## Examples

``` r
## Load MSFT Open Prices  - 
   INDEX <- MSFT[1:20, 1]
   INDEX
#> GMT 
#>               Open
#> 2000-09-27 63.4375
#> 2000-09-28 60.8125
#> 2000-09-29 61.0000
#> 2000-10-02 60.5000
#> 2000-10-03 59.5625
#> 2000-10-04 56.3750
#> 2000-10-05 55.5000
#> 2000-10-06 55.8125
#> 2000-10-09 55.6250
#> 2000-10-10 53.9375
#> 2000-10-11 54.0000
#> 2000-10-12 56.3125
#> 2000-10-13 53.8750
#> 2000-10-16 53.5000
#> 2000-10-17 51.8750
#> 2000-10-18 49.6250
#> 2000-10-19 58.4375
#> 2000-10-20 61.3125
#> 2000-10-23 64.6250
#> 2000-10-24 62.6250
   
## Compute Wealth Normalized to 100 - 
   100 * index2wealth(INDEX)
#> GMT 
#>                 Open
#> 2000-09-27 100.00000
#> 2000-09-28  95.86207
#> 2000-09-29  96.15764
#> 2000-10-02  95.36946
#> 2000-10-03  93.89163
#> 2000-10-04  88.86700
#> 2000-10-05  87.48768
#> 2000-10-06  87.98030
#> 2000-10-09  87.68473
#> 2000-10-10  85.02463
#> 2000-10-11  85.12315
#> 2000-10-12  88.76847
#> 2000-10-13  84.92611
#> 2000-10-16  84.33498
#> 2000-10-17  81.77340
#> 2000-10-18  78.22660
#> 2000-10-19  92.11823
#> 2000-10-20  96.65025
#> 2000-10-23 101.87192
#> 2000-10-24  98.71921
```
