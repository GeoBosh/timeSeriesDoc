# Transpose 'timeSeries' objects

Returns the transpose of a `"timeSeries"` object.

## Usage

``` r
# S4 method for class 'timeSeries'
t(x)
```

## Arguments

- x:

  a 'timeSeries' object.

## Value

a matrix

## Examples

``` r
## Dummy 'timeSeries' with NAs entries
   data <- matrix(1:24, ncol = 2)
   s <- timeSeries(data, timeCalendar())
   s
#> GMT 
#>            TS.1 TS.2
#> 2025-01-01    1   13
#> 2025-02-01    2   14
#> 2025-03-01    3   15
#> 2025-04-01    4   16
#> 2025-05-01    5   17
#> 2025-06-01    6   18
#> 2025-07-01    7   19
#> 2025-08-01    8   20
#> 2025-09-01    9   21
#> 2025-10-01   10   22
#> 2025-11-01   11   23
#> 2025-12-01   12   24
   
## Transpose 'timeSeries' -
   t(s)
#>      [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12]
#> TS.1    1    2    3    4    5    6    7    8    9    10    11    12
#> TS.2   13   14   15   16   17   18   19   20   21    22    23    24
```
