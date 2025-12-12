# Methods for 'window' in package 'timeSeries'

Extract a part from a `"timeSeries"` object.

## Usage

``` r
# S3 method for class 'timeSeries'
window(x, start, end, ...)
```

## Arguments

- x:

  an object of class `"timeSeries"`.

- start, end:

  starting date and end date, `end` must be after `start`.

- ...:

  arguments passed to other methods.

## Details

`window` extracts the subset of the `"timeSeries"` object `x` observed
between the times `start` and `end`.

## See also

[`head`](https://geobosh.github.io/timeSeriesDoc/reference/base-subsetting.md),
[`outlier`](https://geobosh.github.io/timeSeriesDoc/reference/base-subsetting.md)

## Examples

``` r
## load LPP benchmark returns
x <- LPP2005REC[, 7:9]
range(time(x))
#> GMT
#> [1] [2005-11-01] [2007-04-11]
  
## extract data for January 2006
window(x, "2006-01-01", "2006-01-31")
#> GMT 
#>                   LPP25        LPP40        LPP60
#> 2006-01-02  0.000165480  0.000297932  0.000444413
#> 2006-01-03  0.000019500 -0.000076900  0.000009450
#> 2006-01-04  0.001847585  0.002227044  0.002945121
#> 2006-01-05 -0.000602521 -0.000805771 -0.001093968
#> 2006-01-06  0.000553944  0.000844125  0.001291886
#> 2006-01-09  0.001844267  0.003025315  0.004325551
#> 2006-01-10 -0.001280919 -0.001540235 -0.001981789
#> 2006-01-11  0.000960843  0.002094522  0.003631846
#> 2006-01-12  0.002548068  0.003119294  0.003796029
#> 2006-01-13 -0.001161811 -0.001200778 -0.001223253
#> 2006-01-16  0.000193729  0.000162094  0.000196195
#> 2006-01-17 -0.001337495 -0.002720934 -0.004437794
#> 2006-01-18 -0.002019320 -0.004157731 -0.006873332
#> 2006-01-19  0.001650710  0.003430897  0.005727921
#> 2006-01-20 -0.002759185 -0.003613313 -0.004887407
#> 2006-01-23 -0.002815600 -0.005072953 -0.007675798
#> 2006-01-24  0.000253631  0.001224870  0.002318423
#> 2006-01-25 -0.000604919  0.000462553  0.001621599
#> 2006-01-26  0.001842887  0.003443139  0.005584311
#> 2006-01-27  0.003394103  0.005791901  0.008762193
#> 2006-01-30  0.001319517  0.002116907  0.003086897
#> 2006-01-31  0.000222982  0.000133349  0.000055900
```
