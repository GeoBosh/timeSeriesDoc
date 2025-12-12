# Cumulated time series from returns

Computes a cumulated financial `"timeSeries"`, e.g. prices or indexes,
from financial returns.

## Usage

``` r
cumulated(x, ...)

# Default S3 method
cumulated(x, method = c("continuous", "discrete", 
    "compound", "simple"), percentage = FALSE, ...)
```

## Arguments

- x:

  an object of class `timeSeries`.

- method:

  a character string, the method for computation of returns.

- percentage:

  a logical value. By default `FALSE`, if `TRUE` the series will be
  expressed in percentage changes.

- ...:

  ignored by the default method.

## Details

Note, the function `cumulated` assumes as input discrete returns from a
price or index series. Only then the cumulated series agrees with the
original price or index series. The first values of the cumulated series
cannot be computed, it is assumed that the series is indexed to 1.

## Value

a `"timeSeries"` object

## See also

[`returns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md),
[`drawdowns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md),
[`splits`](https://geobosh.github.io/timeSeriesDoc/reference/fin-splits.md),
[`midquotes`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md),
[`index2wealth`](https://geobosh.github.io/timeSeriesDoc/reference/fin-wealth.md)

## Examples

``` r
## Use the Microsofts' Close Prices Indexed to 1 - 
   MSFT.CL <- MSFT[, "Close"]
   MSFT.CL <- MSFT.CL/MSFT[[1, "Close"]]
   head(MSFT.CL)
#> GMT 
#>                Close
#> 2000-09-27 1.0000000
#> 2000-09-28 1.0113402
#> 2000-09-29 0.9948454
#> 2000-10-02 0.9752577
#> 2000-10-03 0.9329897
#> 2000-10-04 0.9144330

## Compute Discrete Return -    
   MSFT.RET <- returns(MSFT.CL, method = "discrete")
   
## Cumulated Series and Compare - 
   MSFT.CUM <- cumulated(MSFT.RET, method = "discrete") 
   head(cbind(MSFT.CL, MSFT.CUM))
#> GMT 
#>              Close.1   Close.2
#> 2000-09-27 1.0000000        NA
#> 2000-09-28 1.0113402 1.0113402
#> 2000-09-29 0.9948454 0.9948454
#> 2000-10-02 0.9752577 0.9752577
#> 2000-10-03 0.9329897 0.9329897
#> 2000-10-04 0.9144330 0.9144330
```
