# End-of-Period series, stats, and benchmarks

Computes periodical statistics back to a given period.

## Usage

``` r
endOfPeriodSeries(x, 
    nYearsBack = c("1y", "2y", "3y", "5y", "10y", "YTD"))

endOfPeriodStats(x, 
    nYearsBack = c("1y", "2y", "3y", "5y", "10y", "YTD"))
    
endOfPeriodBenchmarks(x, benchmark = ncol(x),
    nYearsBack = c("1y", "2y", "3y", "5y", "10y", "YTD"))
```

## Arguments

- x:

  an end-of-month recorded multivariate `"timeSeries"` object. One of
  the columns holds the benchmark series specified by argument
  `benchmark`,

- nYearsBack:

  a period string. How long back should the series be treated? Options
  include values from 1 year to 10 years, and year-to-date: "1y", "2y",
  "3y", "5y", "10y", "YTD".

- benchmark:

  an integer giving the position of the benchmark series in `x`. By
  default this is the last column of `x`.

## Details

`endOfPeriodSeries` extract the data for the last few years, as
specified by argument `nYearsBack`.

`endOfPeriodStats` computes basic exploratory statistics for the last
few years in the data.

`endOfPeriodBenchmarks` returns benchmarks back to a given period.

`x` must be end of month data. Such series can be created using
functions like `align`, `alignDailySeries`, `daily2monthly`.

## Value

for `endOfPeriodSeries`, a `"timeSeries"`,

for `endOfPeriodStats`, a data frame,

for `endOfPeriodBenchmarks` - currently `NULL` (invisibly), the function
is unfinished.

## Examples

``` r
## load series: column 1:3 Swiss market, column 8 (4) benchmark
x <- 100 * LPP2005REC[, c(1:3, 8)]
colnames(x)
#> [1] "SBI"   "SPI"   "SII"   "LPP40"
x <- daily2monthly(x)
x
#> GMT 
#>                   SBI        SPI        SII      LPP40
#> 2005-11-30  0.0613921 -0.4037055  0.1711131 -0.1711835
#> 2005-12-31 -0.0456934 -0.3976473 -0.1299026 -0.1363995
#> 2006-01-31 -0.0152952  0.2736095  0.2868720  0.0133349
#> 2006-02-28  0.1071074 -1.1956984  0.1659104 -0.4868522
#> 2006-03-31  0.0232369 -0.0929251 -0.3742188  0.1108179
#> 2006-04-30  0.1330360 -0.2943741  0.2043796 -0.2990218
#> 2006-05-31  0.0233945  0.9323326  0.4888790  0.2653102
#> 2006-06-30 -0.0548353  1.4473814  0.0000000  0.1466710
#> 2006-07-31  0.0077800  0.0267236  0.4459707  0.0642307
#> 2006-08-31  0.0921518 -0.1466397  0.3750473  0.2126960
#> 2006-09-30 -0.1218862  0.1409431  0.3622828  0.0731769
#> 2006-10-31  0.2819157 -0.8238610  0.1611929  0.0018300
#> 2006-11-30  0.0453412 -0.8646808  0.0949359 -0.1401989
#> 2006-12-31  0.1144121 -0.1101976 -0.2031734 -0.0341003
#> 2007-01-31 -0.0306326 -0.0064900  0.0047200 -0.0512010
#> 2007-02-28  0.0380648 -1.1946524 -0.0285334 -0.3741769
#> 2007-03-31 -0.0305670  0.0497094 -0.1809619  0.0943400
#> 2007-04-30  0.0306279 -0.1044170 -0.1339276 -0.0586108
   
## Get the Monthly Series - 
endOfPeriodSeries(x, nYearsBack="1y")
#> GMT 
#>                   SBI        SPI        SII      LPP40
#> 2006-05-31  0.0233945  0.9323326  0.4888790  0.2653102
#> 2006-06-30 -0.0548353  1.4473814  0.0000000  0.1466710
#> 2006-07-31  0.0077800  0.0267236  0.4459707  0.0642307
#> 2006-08-31  0.0921518 -0.1466397  0.3750473  0.2126960
#> 2006-09-30 -0.1218862  0.1409431  0.3622828  0.0731769
#> 2006-10-31  0.2819157 -0.8238610  0.1611929  0.0018300
#> 2006-11-30  0.0453412 -0.8646808  0.0949359 -0.1401989
#> 2006-12-31  0.1144121 -0.1101976 -0.2031734 -0.0341003
#> 2007-01-31 -0.0306326 -0.0064900  0.0047200 -0.0512010
#> 2007-02-28  0.0380648 -1.1946524 -0.0285334 -0.3741769
#> 2007-03-31 -0.0305670  0.0497094 -0.1809619  0.0943400
#> 2007-04-30  0.0306279 -0.1044170 -0.1339276 -0.0586108
   
## Compute the Monthly Statistics
endOfPeriodStats(x, nYearsBack="1y")
#>                        SBI         SPI         SII       LPP40
#> nobs           12.00000000 12.00000000 12.00000000 12.00000000
#> NAs             0.00000000  0.00000000  0.00000000  0.00000000
#> Minimum        -0.12188620 -1.19465240 -0.20317340 -0.37417690
#> Maximum         0.28191570  1.44738140  0.48887900  0.26531020
#> 1. Quartile    -0.03058340 -0.31594502 -0.05488195 -0.05305345
#> 3. Quartile     0.05704385  0.07251783  0.36547392  0.10742275
#> Mean            0.03298057 -0.05448737  0.11553603  0.01666391
#> Median          0.02701120 -0.05545350  0.04982795  0.03303035
#> Sum            -1.16378990 -1.16378990 -1.16378990 -1.16378990
#> SE Mean         0.02923163  0.21051500  0.07163748  0.04916552
#> LCL Mean       -0.03135781 -0.51782776 -0.04213701 -0.09154867
#> UCL Mean        0.09731896  0.40885302  0.27320906  0.12487648
#> Variance        0.01025386  0.53179878  0.06158315  0.02900698
#> Stdev           0.10126133  0.72924535  0.24815952  0.17031435
#> Skewness        0.90313679  0.40555349  0.22273611 -0.65071051
#> Kurtosis        0.61746808 -0.49271933 -1.63160327 -0.06477968
#> worstPeriod    -1.19569840 -1.19569840 -1.19569840 -1.19569840
#> negativeValues 33.00000000 33.00000000 33.00000000 33.00000000
#> positiveValues 38.00000000 38.00000000 38.00000000 38.00000000
   
## Compute the Benchmark
endOfPeriodBenchmarks(x, benchmark=4) 
```
