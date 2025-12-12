# Subsetting time series

Objects from class `"timeSeries"` can be subsetted in different ways.
Methods are defined for the subsetting operators `"$"`, `"["` and their
assignment versions, as well as for some related functions from base R.
A function to drop or extract outliers is also described here.

## Usage

``` r
# S3 method for class 'timeSeries'
head(x, n = 6, recordIDs = FALSE, ...)
# S3 method for class 'timeSeries'
tail(x, n = 6, recordIDs = FALSE, ...)

outlier(x, sd = 5, complement = TRUE, ...)
```

## Arguments

- x:

  an object of class `timeSeries`.

&nbsp;

- n:

  an integer specifying the number of lines to be returned. By default
  `n=6`.

- recordIDs:

  a logical value. Should the `recordIDs` be returned together with the
  data matrix and time series positions?

- sd:

  a numeric value of standard deviations, e.g. 10 means that values
  larger or smaller than ten times the standard deviation will be
  removed from the series.

- complement:

  a logical flag. If `TRUE`, the default, return the series free of
  outliers. If `FALSE`, return the outliers series.

&nbsp;

- ...:

  arguments passed to other methods.

## Details

The `"timeSeries"` methods for the subsetting operators `"$"`, `"["` and
their assignment versions, as well as for the functions `head` and
`tail` are meant to do what the user expects.

**TODO:** Further details are needed here, despite the above paragraph.

`outlier` drops the outliers if `complement = TRUE` and returns only
them if `complement = FALSE`.

All functions described here return `"timeSeries"` objects.

See also
[`window`](https://geobosh.github.io/timeSeriesDoc/reference/stats-window.md)
which extracts the sub-series between two datetimes.

## Value

All functions return an object of class `"timeSeries"`.

## See also

[`window`](https://geobosh.github.io/timeSeriesDoc/reference/stats-window.md)

## Examples

``` r
## Create an Artificial 'timeSeries' Object
setRmetricsOptions(myFinCenter = "GMT")
charvec <- timeCalendar()
set.seed(4711)
data <- matrix(exp(cumsum(rnorm(12, sd = 0.1))))
tS <- timeSeries(data, charvec, units = "tS")
tS
#> GMT 
#>                   tS
#> 2025-01-01 1.1995824
#> 2025-02-01 1.3757753
#> 2025-03-01 1.5506114
#> 2025-04-01 1.4887865
#> 2025-05-01 1.4005479
#> 2025-06-01 1.2043889
#> 2025-07-01 1.3069906
#> 2025-08-01 1.1867998
#> 2025-09-01 1.1815277
#> 2025-10-01 1.2389245
#> 2025-11-01 1.1230263
#> 2025-12-01 0.9596526
   
## Subset Series by Counts "["
tS[1:3, ]
#> GMT 
#>                  tS
#> 2025-01-01 1.199582
#> 2025-02-01 1.375775
#> 2025-03-01 1.550611
       
## Subset the Head of the Series
head(tS, 6)
#> GMT 
#>                  tS
#> 2025-01-01 1.199582
#> 2025-02-01 1.375775
#> 2025-03-01 1.550611
#> 2025-04-01 1.488787
#> 2025-05-01 1.400548
#> 2025-06-01 1.204389
```
