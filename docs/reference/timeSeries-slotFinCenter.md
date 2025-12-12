# Get and set Financial center of a 'timeSeries'

Get or assign a financial center to a `"timeSeries"` object.

## Usage

``` r
# S4 method for class 'timeSeries'
finCenter(x)
# S4 method for class 'timeSeries'
finCenter(x) <- value

getFinCenter(x)         
setFinCenter(x) <- value
```

## Arguments

- x:

  a `"timeSeries"` object.

- value:

  a character with the the location of the financial center named as
  `"continent/city"`.

## See also

[`listFinCenter`](https://geobosh.github.io/timeDateDoc/reference/timeDate-listFinCenter.html)
and
[`finCenter`](https://geobosh.github.io/timeDateDoc/reference/timeDate-finCenter.html)
in package `"timeDate"`

## Examples

``` r
## An artificial 'timeSeries' Object - 
   tS <- dummyMonthlySeries()
   tS
#> GMT 
#>                  TS.1      TS.2
#> 2025-01-01 0.52569755 0.9921504
#> 2025-02-01 0.91465817 0.8073523
#> 2025-03-01 0.83134505 0.5533336
#> 2025-04-01 0.04577026 0.6464061
#> 2025-05-01 0.45609148 0.3118243
#> 2025-06-01 0.26518667 0.6218192
#> 2025-07-01 0.30467220 0.3297702
#> 2025-08-01 0.50730687 0.5019975
#> 2025-09-01 0.18109621 0.6770945
#> 2025-10-01 0.75967064 0.4849912
#> 2025-11-01 0.20124804 0.2439288
#> 2025-12-01 0.25880982 0.7654598

## Print Financial Center -
   finCenter(tS)
#> [1] "GMT"
   getFinCenter(tS)
#> [1] "GMT"

## Assign New Financial Center - 
   finCenter(tS) <- "Zurich"
   tS
#> Zurich 
#>                           TS.1      TS.2
#> 2025-01-01 01:00:00 0.52569755 0.9921504
#> 2025-02-01 01:00:00 0.91465817 0.8073523
#> 2025-03-01 01:00:00 0.83134505 0.5533336
#> 2025-04-01 02:00:00 0.04577026 0.6464061
#> 2025-05-01 02:00:00 0.45609148 0.3118243
#> 2025-06-01 02:00:00 0.26518667 0.6218192
#> 2025-07-01 02:00:00 0.30467220 0.3297702
#> 2025-08-01 02:00:00 0.50730687 0.5019975
#> 2025-09-01 02:00:00 0.18109621 0.6770945
#> 2025-10-01 02:00:00 0.75967064 0.4849912
#> 2025-11-01 01:00:00 0.20124804 0.2439288
#> 2025-12-01 01:00:00 0.25880982 0.7654598
   setFinCenter(tS) <- "New_York"
   tS
#> New_York 
#>                           TS.1      TS.2
#> 2024-12-31 19:00:00 0.52569755 0.9921504
#> 2025-01-31 19:00:00 0.91465817 0.8073523
#> 2025-02-28 19:00:00 0.83134505 0.5533336
#> 2025-03-31 20:00:00 0.04577026 0.6464061
#> 2025-04-30 20:00:00 0.45609148 0.3118243
#> 2025-05-31 20:00:00 0.26518667 0.6218192
#> 2025-06-30 20:00:00 0.30467220 0.3297702
#> 2025-07-31 20:00:00 0.50730687 0.5019975
#> 2025-08-31 20:00:00 0.18109621 0.6770945
#> 2025-09-30 20:00:00 0.75967064 0.4849912
#> 2025-10-31 20:00:00 0.20124804 0.2439288
#> 2025-11-30 19:00:00 0.25880982 0.7654598
```
