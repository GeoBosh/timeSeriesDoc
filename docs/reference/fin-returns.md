# Financial returns

Compute financial returns from prices or indexes.

## Usage

``` r
returns(x, ...)
returns0(x, ...)

# S4 method for class 'ANY'
returns(x, method = c("continuous", "discrete", 
    "compound", "simple"), percentage = FALSE, ...)
# S4 method for class 'timeSeries'
returns(x, method = c("continuous", "discrete", 
    "compound", "simple"), percentage = FALSE, na.rm = TRUE, 
    trim = TRUE, ...)
```

## Arguments

- x:

  an object of class `timeSeries`.

- method:

  a character string. Which method should be used to compute the
  returns, one of "continuous", "discrete", or "compound", "simple". The
  second pair of methods is a synonym for the first two methods.

- percentage:

  a logical value. By default `FALSE`, if `TRUE` the series will be
  expressed in percentage changes.

- na.rm:

  a logical value. Should NAs be removed? By default `TRUE`.

- trim:

  a logical value. Should the time series be trimmed? By Default `TRUE`.

- ...:

  arguments to be passed.

## Value

an object of class `timeSeries`.

`returns0` returns an untrimmed series with the first row of returns set
to zero(s).

## Note

The functions `returnSeries` and `getReturns` will be removed in the
near future. They are synonyms for the function `returns` and their use
was discouraged for many years. Just use `returns`.

The function `returnSeries` is no longer exported. `getReturns` is
exported only because we are waiting for a package on CRAN to be
updated.

## See also

[`cumulated`](https://geobosh.github.io/timeSeriesDoc/reference/fin-cumulated.md),
[`drawdowns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md),
[`splits`](https://geobosh.github.io/timeSeriesDoc/reference/fin-splits.md),
[`spreads`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md),
[`midquotes`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md),
[`index2wealth`](https://geobosh.github.io/timeSeriesDoc/reference/fin-wealth.md)

## Examples

``` r
## Load Microsoft Data - 
   setRmetricsOptions(myFinCenter = "GMT")
   data(MSFT)
   X = MSFT[1:10, 1:4]
   X
#> GMT 
#>               Open    High     Low   Close
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375
#> 2000-10-05 55.5000 57.2500 55.2500 55.3750
#> 2000-10-06 55.8125 56.7500 54.7500 55.5625
#> 2000-10-09 55.6250 55.7500 53.0000 54.1875
#> 2000-10-10 53.9375 55.5625 53.8125 54.5625

## Continuous Returns - 
   returns(X)
#> GMT 
#>                    Open         High          Low        Close
#> 2000-09-28 -0.042259809 -0.026907453  0.013492680  0.011276388
#> 2000-09-29  0.003078504 -0.009132484 -0.033546122 -0.016444358
#> 2000-10-02 -0.008230499 -0.008188377 -0.006417134 -0.019885532
#> 2000-10-03 -0.015617184 -0.016580691 -0.030503454 -0.044307625
#> 2000-10-04 -0.055000384 -0.055868448 -0.036039936 -0.020089961
#> 2000-10-05 -0.015642777  0.012081421  0.013667639 -0.001128032
#> 2000-10-06  0.005614838 -0.008771986 -0.009090972  0.003380285
#> 2000-10-09 -0.003365118 -0.017778246 -0.032485455 -0.025058259
#> 2000-10-10 -0.030806772 -0.003368897  0.015213869  0.006896579
   returns0(X)
#> GMT 
#>                    Open         High          Low        Close
#> 2000-09-27  0.000000000  0.000000000  0.000000000  0.000000000
#> 2000-09-28 -0.042259809 -0.026907453  0.013492680  0.011276388
#> 2000-09-29  0.003078504 -0.009132484 -0.033546122 -0.016444358
#> 2000-10-02 -0.008230499 -0.008188377 -0.006417134 -0.019885532
#> 2000-10-03 -0.015617184 -0.016580691 -0.030503454 -0.044307625
#> 2000-10-04 -0.055000384 -0.055868448 -0.036039936 -0.020089961
#> 2000-10-05 -0.015642777  0.012081421  0.013667639 -0.001128032
#> 2000-10-06  0.005614838 -0.008771986 -0.009090972  0.003380285
#> 2000-10-09 -0.003365118 -0.017778246 -0.032485455 -0.025058259
#> 2000-10-10 -0.030806772 -0.003368897  0.015213869  0.006896579
  
## Discrete Returns:
   returns(X, method = "discrete")
#> GMT 
#>                    Open         High          Low        Close
#> 2000-09-28 -0.041379310 -0.026548673  0.013584117  0.011340206
#> 2000-09-29  0.003083248 -0.009090909 -0.032989691 -0.016309888
#> 2000-10-02 -0.008196721 -0.008154944 -0.006396588 -0.019689119
#> 2000-10-03 -0.015495868 -0.016443988 -0.030042918 -0.043340381
#> 2000-10-04 -0.053515215 -0.054336468 -0.035398230 -0.019889503
#> 2000-10-05 -0.015521064  0.012154696  0.013761468 -0.001127396
#> 2000-10-06  0.005630631 -0.008733624 -0.009049774  0.003386005
#> 2000-10-09 -0.003359462 -0.017621145 -0.031963470 -0.024746907
#> 2000-10-10 -0.030337079 -0.003363229  0.015330189  0.006920415
   
## Don't trim:
   returns(X, trim = FALSE)
#> GMT 
#>                    Open         High          Low        Close
#> 2000-09-27           NA           NA           NA           NA
#> 2000-09-28 -0.042259809 -0.026907453  0.013492680  0.011276388
#> 2000-09-29  0.003078504 -0.009132484 -0.033546122 -0.016444358
#> 2000-10-02 -0.008230499 -0.008188377 -0.006417134 -0.019885532
#> 2000-10-03 -0.015617184 -0.016580691 -0.030503454 -0.044307625
#> 2000-10-04 -0.055000384 -0.055868448 -0.036039936 -0.020089961
#> 2000-10-05 -0.015642777  0.012081421  0.013667639 -0.001128032
#> 2000-10-06  0.005614838 -0.008771986 -0.009090972  0.003380285
#> 2000-10-09 -0.003365118 -0.017778246 -0.032485455 -0.025058259
#> 2000-10-10 -0.030806772 -0.003368897  0.015213869  0.006896579
   
## Use Percentage Values:
   returns(X, percentage = TRUE, trim = FALSE)
#> GMT 
#>                  Open       High        Low      Close
#> 2000-09-27         NA         NA         NA         NA
#> 2000-09-28 -4.2259809 -2.6907453  1.3492680  1.1276388
#> 2000-09-29  0.3078504 -0.9132484 -3.3546122 -1.6444358
#> 2000-10-02 -0.8230499 -0.8188377 -0.6417134 -1.9885532
#> 2000-10-03 -1.5617184 -1.6580691 -3.0503454 -4.4307625
#> 2000-10-04 -5.5000384 -5.5868448 -3.6039936 -2.0089961
#> 2000-10-05 -1.5642777  1.2081421  1.3667639 -0.1128032
#> 2000-10-06  0.5614838 -0.8771986 -0.9090972  0.3380285
#> 2000-10-09 -0.3365118 -1.7778246 -3.2485455 -2.5058259
#> 2000-10-10 -3.0806772 -0.3368897  1.5213869  0.6896579
```
