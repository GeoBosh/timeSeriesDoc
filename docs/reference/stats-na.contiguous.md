# Find longest contiguous stretch of non-NAs or check for NAs

Find the longest consecutive stretch of non-missing values in a
`"timeSeries"` object. In the event of a tie, the first such stretch.
Also, `"timeSeries"` method for `is.na`.

## Usage

``` r
# S3 method for class 'timeSeries'
na.contiguous(object, ...)
# S4 method for class 'timeSeries'
is.na(x)
```

## Arguments

- object,x:

  a `"timeSeries"` object.

- ...:

  further arguments passed to other methods.

## Value

for the `na.contiguous` method, a `"timeSeries"` object without missing
values,

for the `is.na` method, a `"timeSeries"` object whose data part is a
logical matrix of the same dimension as in `x` indicating if the
corresponding values are `NA` or not.

## Examples

``` r
## Dummy 'timeSeries' containing NAs
data <- matrix(sample(c(1:20, rep(NA,4))), ncol = 2)
s <- timeSeries(data, timeCalendar(2023))
is.na(s)  
#> GMT 
#>             TS.1  TS.2
#> 2023-01-01  TRUE FALSE
#> 2023-02-01 FALSE FALSE
#> 2023-03-01 FALSE FALSE
#> 2023-04-01 FALSE FALSE
#> 2023-05-01 FALSE FALSE
#> 2023-06-01 FALSE FALSE
#> 2023-07-01 FALSE FALSE
#> 2023-08-01 FALSE FALSE
#> 2023-09-01 FALSE FALSE
#> 2023-10-01  TRUE FALSE
#> 2023-11-01 FALSE  TRUE
#> 2023-12-01  TRUE FALSE
## Find the longest consecutive non-missing values
na.contiguous(s)
#> GMT 
#>            TS.1 TS.2
#> 2023-02-01   16    5
#> 2023-03-01   15   20
#> 2023-04-01    9   17
#> 2023-05-01    8    3
#> 2023-06-01   19    7
#> 2023-07-01   12   11
#> 2023-08-01    2    4
#> 2023-09-01    1    6

## tied longest stretches: 1:3, 6:9 and 10:12
x <- c(1:3, NA, NA, 6:8, NA, 10:12)
## should return the 1st one
na.contiguous(x)             # correct for R > 4.3.0
#> [1] 1 2 3
#> attr(,"na.action")
#> [1]  4  5  6  7  8  9 10 11 12
#> attr(,"class")
#> [1] "omit"
na.contiguous(timeSeries(x)) # correct for timeSeries version > 4030.106 
#>  
#>      SS.1
#> [1,]    1
#> [2,]    2
#> [3,]    3
```
