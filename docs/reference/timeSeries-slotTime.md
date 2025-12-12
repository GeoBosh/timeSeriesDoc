# Get and set time stamps of a 'timeSeries'

Functions and methods extracting and modifying positions of 'timeSeries'
objects.

## Usage

``` r
# S4 method for class 'timeSeries'
time(x, ...)
# S3 method for class 'timeSeries'
time(x) <- value

getTime(x)         
setTime(x) <- value
```

## Arguments

- value:

  a valid value for the time component of `x`.

- x:

  an object of class `timeSeries`.

- ...:

  optional arguments passed to other methods.

## Details

`time` and `time<-` are generic functions with methods for class
`"timeSeries"`. They get and set the time component of the object.

`getTime` and `setTime` are non-generic alternatives are non-generic
wrappers of `time` and `time<-`, respectively.

There is another generic function `time<-` defined in package zoo. When
that package is loaded its `time<-` gets the `"timeSeries"` method.
Also, if `"time<-"` is called with an object from class other than
`"timeSeries"`, the call is dispatched to `"zoo:time<-"` to apply a
suitable method.

## Value

for `time` and `getTime`, a `"timeDate"` object,

for `time<-` and and `setTime`, the modified `"timeSeries"` object.

## Examples

``` r
## Create Dummy 'timeSeries' -      
   X <- timeSeries(matrix(rnorm(24), 12), timeCalendar())
   
## Return Series Positions -
   getTime(X)
#> GMT
#>  [1] [2025-01-01] [2025-02-01] [2025-03-01] [2025-04-01] [2025-05-01]
#>  [6] [2025-06-01] [2025-07-01] [2025-08-01] [2025-09-01] [2025-10-01]
#> [11] [2025-11-01] [2025-12-01]
   time(X)  
#> GMT
#>  [1] [2025-01-01] [2025-02-01] [2025-03-01] [2025-04-01] [2025-05-01]
#>  [6] [2025-06-01] [2025-07-01] [2025-08-01] [2025-09-01] [2025-10-01]
#> [11] [2025-11-01] [2025-12-01]
  
## Add / Subtract one Day from X
   setTime(X) <- time(X) - 24*3600 # sec
   X
#> GMT 
#>                   TS.1         TS.2
#> 2024-12-31 -0.58207592 -0.669633580
#> 2025-01-31 -1.10888962 -0.007604756
#> 2025-02-28 -1.01496201  1.777084448
#> 2025-03-31 -0.16230952 -1.138607737
#> 2025-04-30  0.56305582  1.367827179
#> 2025-05-31  1.64781747  1.329564791
#> 2025-06-30 -0.77335342  0.336472797
#> 2025-07-31  1.60590963  0.006892838
#> 2025-08-31 -1.15780855 -0.455468738
#> 2025-09-30  0.65658846 -0.366523933
#> 2025-10-31  2.54899107  0.648286568
#> 2025-11-30 -0.03476039  2.070270861
   time(X) <- time(X) + 24*3600 # sec
   X
#> GMT 
#>                   TS.1         TS.2
#> 2025-01-01 -0.58207592 -0.669633580
#> 2025-02-01 -1.10888962 -0.007604756
#> 2025-03-01 -1.01496201  1.777084448
#> 2025-04-01 -0.16230952 -1.138607737
#> 2025-05-01  0.56305582  1.367827179
#> 2025-06-01  1.64781747  1.329564791
#> 2025-07-01 -0.77335342  0.336472797
#> 2025-08-01  1.60590963  0.006892838
#> 2025-09-01 -1.15780855 -0.455468738
#> 2025-10-01  0.65658846 -0.366523933
#> 2025-11-01  2.54899107  0.648286568
#> 2025-12-01 -0.03476039  2.070270861
```
