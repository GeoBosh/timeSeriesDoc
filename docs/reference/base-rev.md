# Reverse a 'timeSeries'

Reverses an uni- or multivariate `"timeSeries"` object.

## Usage

``` r
# S3 method for class 'timeSeries'
rev(x)
```

## Arguments

- x:

  an uni- or multivariate `"timeSeries"` object.

## Value

a `"timeSeries"` object

## Examples

``` r
## Create Dummy "timeSeries"
tS <- dummyMonthlySeries()
   
## reverse series
rev(tS)
#> GMT 
#>                   TS.1       TS.2
#> 2025-12-01 0.544974836 0.03999592
#> 2025-11-01 0.693591292 0.15904600
#> 2025-10-01 0.514251141 0.30269337
#> 2025-09-01 0.666083758 0.31661245
#> 2025-08-01 0.232550506 0.23222591
#> 2025-07-01 0.009495756 0.18672279
#> 2025-06-01 0.640310605 0.26682078
#> 2025-05-01 0.860915384 0.28622328
#> 2025-04-01 0.623379442 0.83729563
#> 2025-03-01 0.609274733 0.29231584
#> 2025-02-01 0.622299405 0.92343348
#> 2025-01-01 0.113703411 0.28273358
```
