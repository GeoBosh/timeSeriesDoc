# Sort a 'timeSeries' by time stamps

Sort a `"timeSeries"` object with respect to its time stamps.

## Usage

``` r
# S3 method for class 'timeSeries'
sort(x, decreasing = FALSE, ...)

# S4 method for class 'timeSeries'
is.unsorted(x, na.rm = FALSE, strictly = FALSE)
```

## Arguments

- x:

  a `"timeSeries"` object.

- decreasing:

  a logical flag. Should we sort in increasing or decreasing order? By
  default `FALSE`.

- na.rm:

  a logical value, should missing values be removed?

- strictly:

  logical indicating if the check should be for strictly increasing
  values.

- ...:

  optional arguments passed to other methods.

## Details

The method for `sort` sorts `x` either in increasing or decreasing time
stamp order.

The method for `is.unsorted` returns `TRUE` if the time stamps of `x`
are not sorted in increasing order (including the case when they are
sorted in decreasing order) and `FALSE` otherwise. `is.unsorted` may
also return `NA` when there are `NA`s among the time stamps of `x`.

All this is in line with the documented functionality of
[`base::is.unsorted`](https://rdrr.io/r/base/is.unsorted.html).

## Value

for `sort`, a `"timeSeries"` object,

for the `is.unsorted` method, `TRUE`, `FALSE`, or `NA`, as described in
section ‘Details’.

## Note

If `is.unsorted` returns `NA` when there are `NA`s in the data but not
in the time stamps use `library{timeSeries}` or call the function as
`timeSeries::is.unsorted`. If you need more details, read the rest of
this note.

[`base::is.unsorted`](https://rdrr.io/r/base/is.unsorted.html) 'sees'
the method for `"timeSeries"` objects when package timeSeries is loaded
(whether or not it is attached). However, due to the way
[`base::is.unsorted`](https://rdrr.io/r/base/is.unsorted.html) is
implemented, it may give wrong answers when there are `NA`'s among the
values of the time series. Developers of packages applying `is.unsorted`
on timeSeries objects should import if from package timeSeries.

The above feature is not a shortcoming of
[`base::is.unsorted`](https://rdrr.io/r/base/is.unsorted.html) but a
consequence of the fact that the timeSeries method is not consistent
with its semantics. For example, it works on the time stamps, while
`is.na` works on the data values.

## See also

[`is.unsorted`](https://rdrr.io/r/base/is.unsorted.html) for further
details on the `NA` case

## Examples

``` r
## a monthly calendar series
x <- daily2monthly(LPP2005REC[, 1:2])[3:14, ]
   
## resample the series with respect to the time stamps,
resampled <- sample(x)
## the time stamps are unordered
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
is.unsorted(resampled) # TRUE (i.e., not sorted)
#> [1] TRUE
   
## Now sort the series in decreasing time order
backward_in_time <- sort(resampled, , decreasing = TRUE)
## time stamps ordered in decreasing order
## but is.unordered requires increasing order:
backward_in_time
#> GMT 
#>                     SBI          SPI
#> 2006-12-31  0.001144121 -0.001101976
#> 2006-11-30  0.000453412 -0.008646808
#> 2006-10-31  0.002819157 -0.008238610
#> 2006-09-30 -0.001218862  0.001409431
#> 2006-08-31  0.000921518 -0.001466397
#> 2006-07-31  0.000077800  0.000267236
#> 2006-06-30 -0.000548353  0.014473814
#> 2006-05-31  0.000233945  0.009323326
#> 2006-04-30  0.001330360 -0.002943741
#> 2006-03-31  0.000232369 -0.000929251
#> 2006-02-28  0.001071074 -0.011956984
#> 2006-01-31 -0.000152952  0.002736095
is.unsorted(backward_in_time) # still TRUE
#> [1] TRUE
   
## Is the reverted series ordered?
forward_in_time <- rev(backward_in_time)
forward_in_time
#> GMT 
#>                     SBI          SPI
#> 2006-01-31 -0.000152952  0.002736095
#> 2006-02-28  0.001071074 -0.011956984
#> 2006-03-31  0.000232369 -0.000929251
#> 2006-04-30  0.001330360 -0.002943741
#> 2006-05-31  0.000233945  0.009323326
#> 2006-06-30 -0.000548353  0.014473814
#> 2006-07-31  0.000077800  0.000267236
#> 2006-08-31  0.000921518 -0.001466397
#> 2006-09-30 -0.001218862  0.001409431
#> 2006-10-31  0.002819157 -0.008238610
#> 2006-11-30  0.000453412 -0.008646808
#> 2006-12-31  0.001144121 -0.001101976
is.unsorted(forward_in_time) # FALSE (i.e., sorted)
#> [1] FALSE
```
