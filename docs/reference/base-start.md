# Start and end of a 'timeSeries'

Returns start or end time stamp of a `"timeSeries"` object.

## Usage

``` r
# S3 method for class 'timeSeries'
start(x, ...)

# S3 method for class 'timeSeries'
end(x, ...)
```

## Arguments

- x:

  an uni- or multivariate `"timeSeries"` object.

- ...:

  optional arguments passed to other methods.

## Value

a `"timeSeries"` object

## Examples

``` r
## Create a dummy \code{"timeSeries"}
tS <- dummyMonthlySeries()[, 1]
tS
#> GMT 
#>                   TS.1
#> 2025-01-01 0.113703411
#> 2025-02-01 0.622299405
#> 2025-03-01 0.609274733
#> 2025-04-01 0.623379442
#> 2025-05-01 0.860915384
#> 2025-06-01 0.640310605
#> 2025-07-01 0.009495756
#> 2025-08-01 0.232550506
#> 2025-09-01 0.666083758
#> 2025-10-01 0.514251141
#> 2025-11-01 0.693591292
#> 2025-12-01 0.544974836
   
## Return start and end time stamp
c(start(tS), end(tS))
#> GMT
#> [1] [2025-01-01] [2025-12-01]
range(time(tS))
#> GMT
#> [1] [2025-01-01] [2025-12-01]
```
