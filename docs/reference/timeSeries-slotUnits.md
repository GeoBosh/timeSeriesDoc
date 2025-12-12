# Get and set unit names of a 'timeSeries'

Gets and sets the column names of a `"timeSeries"` object. The column
names are also called units or unit names.

## Usage

``` r
getUnits(x)         
setUnits(x) <- value
```

## Arguments

- x:

  a `"timeSeries"` object.

- value:

  a character vector of unit names.

## See also

[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md)

## Examples

``` r
## A Dummy 'timeSeries' Object
   tS <- dummyMonthlySeries()
   tS
#> GMT 
#>                  TS.1       TS.2
#> 2025-01-01 0.08215807 0.08498474
#> 2025-02-01 0.85026492 0.63729826
#> 2025-03-01 0.23466126 0.43101637
#> 2025-04-01 0.98816745 0.07271609
#> 2025-05-01 0.60189755 0.80240202
#> 2025-06-01 0.99874081 0.32527830
#> 2025-07-01 0.37559938 0.75728904
#> 2025-08-01 0.55512663 0.58427152
#> 2025-09-01 0.42944396 0.70883941
#> 2025-10-01 0.57587778 0.42697577
#> 2025-11-01 0.43250740 0.34357270
#> 2025-12-01 0.22484576 0.75911999

## Get the Units - 
   getUnits(tS)
#> [1] "TS.1" "TS.2"

## Assign New Units to the Series - 
   setUnits(tS) <- c("A", "B")
   head(tS)
#> GMT 
#>                     A          B
#> 2025-01-01 0.08215807 0.08498474
#> 2025-02-01 0.85026492 0.63729826
#> 2025-03-01 0.23466126 0.43101637
#> 2025-04-01 0.98816745 0.07271609
#> 2025-05-01 0.60189755 0.80240202
#> 2025-06-01 0.99874081 0.32527830
```
