# Resample 'timeSeries' objects

Takes a sample of the specified size from the elements of a
`"timeSeries"`.

## Usage

``` r
# S4 method for class 'timeSeries'
sample(x, size, replace = FALSE, prob = NULL)
```

## Arguments

- x:

  an object from class `"timeSeries"`.

- size:

  a non-negative integer giving the number of items to choose.

- replace:

  sample with replacement if `TRUE`, otherwise without replacement.

- prob:

  a vector of probability weights for obtaining the elements of the
  vector being sampled.

## Details

The function takes a sample of size `size` from the elements of the time
series with or without replacement depending on argument `replace`. The
result is returned as a `"timeSeries"` object.

For details about the arguments see the documentation of `base:sample`.

## Value

an object from class `"timeSeries"`

## See also

[`sample`](https://rdrr.io/r/base/sample.html) (`sample` in base R),

[`sample`](https://geobosh.github.io/timeDateDoc/reference/base-sample.html)
(the `"timeDate"` method)

## Examples

``` r
## Monthly Calendar Series -    
   x <- daily2monthly(LPP2005REC[, 1:2])[3:14, ]
   
## Resample the Series with respect to the time stamps -    
   resampled <- sample(x)
   resampled
#> GMT 
#>                     SBI          SPI
#> 2006-12-31  0.001144121 -0.001101976
#> 2006-10-31  0.002819157 -0.008238610
#> 2006-06-30 -0.000548353  0.014473814
#> 2006-05-31  0.000233945  0.009323326
#> 2006-04-30  0.001330360 -0.002943741
#> 2006-07-31  0.000077800  0.000267236
#> 2006-01-31 -0.000152952  0.002736095
#> 2006-09-30 -0.001218862  0.001409431
#> 2006-02-28  0.001071074 -0.011956984
#> 2006-08-31  0.000921518 -0.001466397
#> 2006-11-30  0.000453412 -0.008646808
#> 2006-03-31  0.000232369 -0.000929251
   is.unsorted(resampled)
#> [1] TRUE
```
