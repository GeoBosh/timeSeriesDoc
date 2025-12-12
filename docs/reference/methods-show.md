# Print 'timeSeries' objects

Print `"timeSeries"` objects.

## Usage

``` r
# S4 method for class 'timeSeries'
show(object)

# S3 method for class 'timeSeries'
print(x, FinCenter = NULL, format = NULL,
    style = c("tS", "h", "ts"), by = c("month", "quarter"), ...)
```

## Arguments

- object,x:

  an object of class `"timeSeries"`.

- FinCenter:

  a character with the the location of the financial center named as
  "continent/city".

- format:

  the format specification of the input character vector, a character
  string with the format in POSIX notation.

- style:

  a character string, one of `"tS"`, `"h"`, or `"ts"`.

- by:

  a character string, one of `"month"`, `"quarter"`.

- ...:

  arguments passed to the print method for the data part, which is a
  `"matrix"` or, in the case of `style = "ts"`, to the print method for
  class `"ts"`.

## Details

`show` does not have additional arguments.

The `print` method allows to modify the way the object is shown by
explicitly calling `print`.

The default for `style` is `tS`. For univariate time series
`style = "h"` causes the object to be printed as a vector with the time
stamps as labels. Finally, `style = "ts"` prints like objects from base
R class `"ts"`, which is suitable for quarterly and monthly time series.

## Value

Prints an object of class `timeSeries`.

## Examples

``` r
## Load Micsrosoft Data
setRmetricsOptions(myFinCenter = "GMT")
LPP <- MSFT[1:12, 1:4]

## Abbreviate Column Names
colnames(LPP) <- abbreviate(colnames(LPP), 6)
   
## Print Data Set
print(LPP)
#> GMT 
#>               Open    High     Low   Close
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375
#> 2000-10-05 55.5000 57.2500 55.2500 55.3750
#> 2000-10-06 55.8125 56.7500 54.7500 55.5625
#> 2000-10-09 55.6250 55.7500 53.0000 54.1875
#> 2000-10-10 53.9375 55.5625 53.8125 54.5625
#> 2000-10-11 54.0000 56.9375 54.0000 55.7500
#> 2000-10-12 56.3125 56.8750 53.8125 54.3750
   
## Alternative Use, Show Data Set
LPP  # equivalently, show(LPP)
#> GMT 
#>               Open    High     Low   Close
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375
#> 2000-10-05 55.5000 57.2500 55.2500 55.3750
#> 2000-10-06 55.8125 56.7500 54.7500 55.5625
#> 2000-10-09 55.6250 55.7500 53.0000 54.1875
#> 2000-10-10 53.9375 55.5625 53.8125 54.5625
#> 2000-10-11 54.0000 56.9375 54.0000 55.7500
#> 2000-10-12 56.3125 56.8750 53.8125 54.3750

## a short subseries to demo 'print'
hC <- head(MSFT[ , "Close"])
class(hC)
#> [1] "timeSeries"
#> attr(,"package")
#> [1] "timeSeries"
print(hC)
#> GMT 
#>              Close
#> 2000-09-27 60.6250
#> 2000-09-28 61.3125
#> 2000-09-29 60.3125
#> 2000-10-02 59.1250
#> 2000-10-03 56.5625
#> 2000-10-04 55.4375
print(hC, style = "h")
#> 2000-09-27 2000-09-28 2000-09-29 2000-10-02 2000-10-03 2000-10-04 
#>    60.6250    61.3125    60.3125    59.1250    56.5625    55.4375 
```
