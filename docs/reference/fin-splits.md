# splits

Searches for outlier splits in a `"timeSeries"` object.

## Usage

``` r
splits(x, sd = 3, complement = TRUE, ...)
```

## Arguments

- x:

  a `"timeSeries"` object.

- sd:

  `numeric(1)`; deviations of how many standard deviations to consider
  too big? Can be fractional. E.g., 5 means that values larger or
  smaller than five times the standard deviation of the series will be
  detected.

- complement:

  a logical flag, should the outlier series or its complements be
  returned?

- ...:

  arguments to be passed.

## Details

This function finds splits in financial price or index series. If a
price or index is splitted we observe a big jump of several standard
deviations in the returns, which is identified usually as an outlier.

## Value

a `"timeSeries"` object

## See also

[`returns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md),
[`cumulated`](https://geobosh.github.io/timeSeriesDoc/reference/fin-cumulated.md),
[`drawdowns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md),
[`spreads`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md),
[`midquotes`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md),
[`index2wealth`](https://geobosh.github.io/timeSeriesDoc/reference/fin-wealth.md)

## Examples

``` r
## Create a Return Series with a Split - 
   data <- runif(12, -1, 1)
   data[6] <- 20
   x <- timeSeries(data, timeCalendar(), units="RUNIF")
   x
#> GMT 
#>                  RUNIF
#> 2025-01-01  0.32781337
#> 2025-02-01 -0.86725243
#> 2025-03-01  0.16026217
#> 2025-04-01 -0.27442816
#> 2025-05-01  0.88502200
#> 2025-06-01 20.00000000
#> 2025-07-01 -0.36096099
#> 2025-08-01 -0.24913208
#> 2025-09-01  0.29574272
#> 2025-10-01 -0.72810981
#> 2025-11-01 -0.40709117
#> 2025-12-01  0.04476414
   
## Search for the Split:
   splits(x, sd=3, complement=TRUE)
#> GMT 
#>                  RUNIF
#> 2025-01-01  0.32781337
#> 2025-02-01 -0.86725243
#> 2025-03-01  0.16026217
#> 2025-04-01 -0.27442816
#> 2025-05-01  0.88502200
#> 2025-07-01 -0.36096099
#> 2025-08-01 -0.24913208
#> 2025-09-01  0.29574272
#> 2025-10-01 -0.72810981
#> 2025-11-01 -0.40709117
#> 2025-12-01  0.04476414
   splits(x, sd=3, complement=FALSE)
#> GMT 
#>            RUNIF
#> 2025-06-01    20
```
