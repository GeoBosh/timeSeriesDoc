# Rolling statistics

Computes rolling mean, min, max and median for a `"timeSeries"` object.

## Usage

``` r
rollStats(x, k, FUN = mean, na.pad = FALSE, 
    align=c("center", "left", "right"), ...)
    
rollMean(x, k, na.pad = FALSE, 
    align = c("center", "left", "right"), ...)
rollMin(x, k, na.pad = FALSE, 
    align = c("center", "left", "right"), ...)
rollMax(x, k, na.pad = FALSE, 
    align = c("center", "left", "right"), ...)
rollMedian(x, k, na.pad = FALSE, 
    align = c("center", "left", "right"), ...)
```

## Arguments

- x:

  an uni- or multivariate `"timeSeries"` object.

- k:

  an integer width of the rolling window. Must be odd for `rollMedian`.

- FUN:

  the function to be rolled.

- na.pad:

  a logical flag. Should NA padding be added at beginning? By default
  `FALSE`.

- align:

  a character string specifying whether the index of the result should
  be left- or right-aligned or centered compared to the rolling window
  of observations. The default choice is set to `align="center"`.

- ...:

  optional arguments to be passed.

## Value

an object of class `"timeSeries"`

## Details

The code in the core of the functions `rollMean`, `rollMin`, `rollMax`,
and `rollMedian` was borrowed from the package `zoo` authored by Achim
Zeileis, Gabor Grothendieck and Felix Andrews.

## Author

Achim Zeileis, Gabor Grothendieck and Felix Andrews for code from the
contributed R package `zoo` used in the functions `rollMean`, `rollMin`,
`rollMax`, and `rollMedian`.

## Examples

``` r
## Use Swiss Pension Fund Data Set of Returns - 
   head(LPP2005REC)
#> GMT 
#>                     SBI          SPI          SII          LMI         MPI
#> 2005-11-01 -0.000612745  0.008414595 -0.003190926 -0.001108882 0.001548062
#> 2005-11-02 -0.002762009  0.002519342 -0.004117638 -0.001175939 0.000342876
#> 2005-11-03 -0.001153092  0.012707292 -0.005209409 -0.000992456 0.010502959
#> 2005-11-04 -0.003235750 -0.000702757 -0.001127165 -0.001198528 0.011679558
#> 2005-11-07  0.001310970  0.006205226 -0.001795839  0.000360366 0.002709618
#> 2005-11-08  0.000539312  0.000329260  0.002103374  0.002327040 0.000346843
#>                     ALT        LPP25        LPP40        LPP60
#> 2005-11-01 -0.002572971 -0.000130008  0.000199980  0.000809672
#> 2005-11-02 -0.001141604 -0.001561421 -0.001120404 -0.000469730
#> 2005-11-03  0.005007442  0.001541418  0.003317548  0.005731589
#> 2005-11-04  0.009482677  0.000439969  0.002421248  0.004838735
#> 2005-11-07  0.004723952  0.001638182  0.002246611  0.003012363
#> 2005-11-08  0.000853619  0.001087309  0.000962708  0.000828043
   SPI <- LPP2005REC[, "SPI"]
   head(SPI)
#> GMT 
#>                     SPI
#> 2005-11-01  0.008414595
#> 2005-11-02  0.002519342
#> 2005-11-03  0.012707292
#> 2005-11-04 -0.000702757
#> 2005-11-07  0.006205226
#> 2005-11-08  0.000329260
   
## Plot Drawdowns - 
   rmean <- rollMean(SPI, k = 10)
   plot(rmean)
```
