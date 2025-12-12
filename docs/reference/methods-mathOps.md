# Mathematical operations on 'timeSeries'

Functions and methods for mathematical operations on `"timeSeries"`.

## Usage

``` r
# S4 method for class 'timeSeries,timeSeries'
Ops(e1, e2)
# S4 method for class 'timeSeries'
Math(x)
# S4 method for class 'timeSeries'
Math2(x, digits)

# S3 method for class 'timeSeries'
quantile(x, ...)
# S3 method for class 'timeSeries'
median(x, na.rm = FALSE, ...)
```

## Arguments

- x:

  an object of class `timeSeries`.

- digits:

  number of digits to be used in 'round' or 'signif'.

- e1, e2:

  at least one of the two objects is from class `"timeSeries"` (for the
  methods described on this page).

- na.rm:

  a logical value: should missing values be removed?

- ...:

  arguments to be passed.

## Details

The methods for the `Math` and `Math2` groups of mathematical functions
return 'timeSeries' objects. Most of them work element-wise on the data
part of the time series with the exception of `cummin`, `cummax`,
`cumsum`, and `cumprod` which work columnwise.

The `Ops` group includes mathematical operators. For the binary
operators methods are defined for pairs of at least one 'timeSeries'
object. These work as expected on the data parts of the arguments. If
the operation gives a value of the same dimension as the data part of
the 'timeSeries' object, it replaces the original data in the object.

There are also methods for `quantile` and `median`.

## Value

the value from a mathematical or logical operation operating on objects
of class `"timeSeries"` or the value computed by a mathematical
function.

## See also

[`colCumXXX`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)

## Examples

``` r
## create an artificial 'timeSeries' object
setRmetricsOptions(myFinCenter = "GMT")
charvec = timeCalendar()
set.seed(4711)
data = matrix(exp(cumsum(rnorm(12, sd = 0.1))))
TS = timeSeries(data, charvec, units = "TS")
TS
#> GMT 
#>                   TS
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

## mathematical operations: | +/- * ^ ...
TS^2
#> GMT 
#>                  TS
#> 2025-01-01 1.438998
#> 2025-02-01 1.892758
#> 2025-03-01 2.404396
#> 2025-04-01 2.216485
#> 2025-05-01 1.961534
#> 2025-06-01 1.450553
#> 2025-07-01 1.708224
#> 2025-08-01 1.408494
#> 2025-09-01 1.396008
#> 2025-10-01 1.534934
#> 2025-11-01 1.261188
#> 2025-12-01 0.920933
TS[2:4]
#> [1] 1.375775 1.550611 1.488787
OR = returns(TS)
OR
#> GMT 
#>                      TS
#> 2025-02-01  0.137043950
#> 2025-03-01  0.119631824
#> 2025-04-01 -0.040687920
#> 2025-05-01 -0.061097880
#> 2025-06-01 -0.150891205
#> 2025-07-01  0.081754941
#> 2025-08-01 -0.096466789
#> 2025-09-01 -0.004452208
#> 2025-10-01  0.047435474
#> 2025-11-01 -0.098216632
#> 2025-12-01 -0.157211053
OR > 0
#> GMT 
#>               TS
#> 2025-02-01  TRUE
#> 2025-03-01  TRUE
#> 2025-04-01 FALSE
#> 2025-05-01 FALSE
#> 2025-06-01 FALSE
#> 2025-07-01  TRUE
#> 2025-08-01 FALSE
#> 2025-09-01 FALSE
#> 2025-10-01  TRUE
#> 2025-11-01 FALSE
#> 2025-12-01 FALSE

## median, quantile
median(TS)
#> [1] 1.221657
quantile(TS)
#>        0%       25%       50%       75%      100% 
#> 1.1995824 1.5042427 1.2556897 1.1958769 0.9596526 

TS[3] <- NA # to demonstrate 'na.rm'
median(TS)   # NA
#> [1] NA
#quantile(TS) # error

median(TS, na.rm = TRUE)   
#> [1] 1.204389
quantile(TS, na.rm = TRUE)
#>        0%       25%       50%       75%      100% 
#> 0.9596526 1.1841637 1.2043889 1.3413830 1.4887865 
```
