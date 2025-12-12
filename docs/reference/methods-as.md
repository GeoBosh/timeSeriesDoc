# Convert objects to/from class 'timeSeries'

Functions and methods dealing with the coercion between `"timeSeries"`
and other classes.

## Usage

``` r
## convert to 'timeSeries'
as.timeSeries(x, ...)

## convert from 'timeSeries' to other classes
# S3 method for class 'timeSeries'
as.ts(x, ...)
# S4 method for class 'timeSeries'
as.matrix(x, ...)
# S4 method for class 'timeSeries'
as.data.frame(x, row.names = NULL, optional = FALSE, ...)
# S4 method for class 'timeSeries'
as.list(x, ...)
```

## Arguments

- x:

  the object to be converted, see Section ‘Details’ for the special case
  when `class(x)` is `"character"`.

- row.names:

  `NULL` or a character vector giving the row names for the data frame.
  Missing values are not allowed.

- optional:

  a logical value. If `TRUE`, setting row names and converting column
  names (to syntactic names) is optional.

- ...:

  arguments passed to other methods.

## Details

Functions to create `"timeSeries"` objects from other objects and to
convert `"timeSeries"` objects to other classes.

`as.timeSeries` is a generic function to convert an object to
`"timeSeries"`. There are specialised methods for the following classes:
`"ts"`, `"data.frame"`, `"character"`, and `"zoo"`. The default method
is equivalent to calling `"timeSeries()"`, so `x` can be of any type
that `"timeSeries()"` accepts.

The `character` method of `as.timeSeries` is special, in that its
contents are parsed and evaluated, then `as.timeSeries` is called on the
returned value (passing also the `"..."` arguments. Care is needed to
avoid infinite recursion here since currently the code doesn't guard
against it.

## Value

for `as.timeSeries`, an object of class `"timeSeries"`.  

for `as.numeric`, `as.data.frame`, `as.matrix`, `as.ts`, `as.list` - a
numeric vector, a data frame, a matrix, an object of class `ts`, or a
`"list"`, respectively.

## See also

[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md),
class
[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-class.md)

## Examples

``` r
## Create an Artificial 'timeSeries' Object
setRmetricsOptions(myFinCenter = "GMT")
charvec <- timeCalendar()
data <- matrix(rnorm(12))
TS <- timeSeries(data, charvec, units = "RAND")
TS
#> GMT 
#>                  RAND
#> 2025-01-01 -0.2620870
#> 2025-02-01 -1.3702965
#> 2025-03-01  0.1962448
#> 2025-04-01 -1.2123556
#> 2025-05-01 -0.1588557
#> 2025-06-01 -0.6683035
#> 2025-07-01  0.8826032
#> 2025-08-01  0.2182945
#> 2025-09-01  1.7655480
#> 2025-10-01  1.1424191
#> 2025-11-01 -0.5911973
#> 2025-12-01 -0.6178305

## Coerce to Vector
as.vector(TS)
#>  [1] -0.2620870 -1.3702965  0.1962448 -1.2123556 -0.1588557 -0.6683035
#>  [7]  0.8826032  0.2182945  1.7655480  1.1424191 -0.5911973 -0.6178305
   
## Coerce to Matrix
as.matrix(TS)
#>                  RAND
#> 2025-01-01 -0.2620870
#> 2025-02-01 -1.3702965
#> 2025-03-01  0.1962448
#> 2025-04-01 -1.2123556
#> 2025-05-01 -0.1588557
#> 2025-06-01 -0.6683035
#> 2025-07-01  0.8826032
#> 2025-08-01  0.2182945
#> 2025-09-01  1.7655480
#> 2025-10-01  1.1424191
#> 2025-11-01 -0.5911973
#> 2025-12-01 -0.6178305
  
## Coerce to Data Frame
as.data.frame(TS)
#>                  RAND
#> 2025-01-01 -0.2620870
#> 2025-02-01 -1.3702965
#> 2025-03-01  0.1962448
#> 2025-04-01 -1.2123556
#> 2025-05-01 -0.1588557
#> 2025-06-01 -0.6683035
#> 2025-07-01  0.8826032
#> 2025-08-01  0.2182945
#> 2025-09-01  1.7655480
#> 2025-10-01  1.1424191
#> 2025-11-01 -0.5911973
#> 2025-12-01 -0.6178305
```
