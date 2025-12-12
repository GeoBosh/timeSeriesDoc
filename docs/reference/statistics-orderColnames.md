# Reorder column names of a time series

Functions and methods dealing with the rearrangement of column names of
'timeSeries' objects.  

|                  |                                                |
|------------------|------------------------------------------------|
| `orderColnames`  | Returns ordered column names of a time Series, |
| `sortColnames`   | Returns sorted column names of a time Series,  |
| `sampleColnames` | Returns sampled column names of a time Series, |
| `statsColnames`  | Returns statistically rearranged column names, |
| `pcaColnames`    | Returns PCA correlation ordered column names,  |
| `hclustColnames` | Returns hierarchical clustered column names.   |

## Usage

``` r
orderColnames(x, ...)
sortColnames(x, ...)  
sampleColnames(x, ...) 
statsColnames(x, FUN = colMeans, ...)
pcaColnames(x, robust = FALSE, ...)
hclustColnames(x, method = c("euclidean", "complete"), ...)
```

## Arguments

- x:

  an object of class `timesSeries` or any other rectangular object which
  can be transformed by the function `as.matrix` into a numeric matrix.

- FUN:

  a character string indicating which statistical function should be
  applied. By default statistical ordering operates on the column means
  of the time series.

- method:

  a character string with two elements. The first determines the choice
  of the distance measure, see
  [`dist`](https://rdrr.io/r/stats/dist.html), and the second determines
  the choice of the agglomeration method, see
  [`hclust`](https://rdrr.io/r/stats/hclust.html).

- robust:

  a logical flag which indicates if robust correlations should be used.

- ...:

  further arguments to be passed to the underlying functions doing the
  main work, see section ‘Details’.

## Details

These functions reorder the column names of a `"timeSeries"` object
according to some statistical measure.

**Statistically Motivated Rearrangement**

The function `statsColnames` rearranges the column names according to a
statical measure. These measure must operate on the columns of the time
series and return a vector of values which can be sorted. Typical
functions ar those listed in help page `colStats` but custom functions
can be used that compute for example risk or any other statistical
measure. The `...` argument allows to pass additional arguments to the
underlying function `FUN`.

**PCA Ordering of the Correlation Matrix**

The function `pcaColnames` rearranges the column names according to the
PCA ordered correlation matrix. The argument `robust` allsows to select
between the use of the standard `cor` and computation of robust
correlations using the function `covMcd` from contributed R package
`robustbase`. The `...` argument allows to pass additional arguments to
the two underlying functions `cor` or `covMcd`. E.g., adding
`method="kendall"` to the argument list calculates Kendall's rank
correlations instead the default which calculates Person's
correlations.  

**Ordering by Hierarchical Clustering**

The function `pcaColnames` uses the hierarchical clustering approach
`hclust` to rearrange the column names of the time series.

## Value

for `orderColnames`, an integer vector representing the permutaion that
will sort the column names,

for the other functions, a character vector giving the rearranged column
names

## Examples

``` r
## Load Swiss Pension Fund Benchmark Data -
   data <- LPP2005REC[,1:6]
   
## Abbreviate Column Names -
   colnames(data)
#> [1] "SBI" "SPI" "SII" "LMI" "MPI" "ALT"

## Sort Alphabetically - 
   sortColnames(data)
#> [1] "ALT" "LMI" "MPI" "SBI" "SII" "SPI"
  
## Sort by Column Names by Hierarchical Clustering -
   hclustColnames(data)
#> [1] "SII" "SBI" "LMI" "SPI" "MPI" "ALT"
   head(data[, hclustColnames(data)])
#> GMT 
#>                     SII          SBI          LMI          SPI         MPI
#> 2005-11-01 -0.003190926 -0.000612745 -0.001108882  0.008414595 0.001548062
#> 2005-11-02 -0.004117638 -0.002762009 -0.001175939  0.002519342 0.000342876
#> 2005-11-03 -0.005209409 -0.001153092 -0.000992456  0.012707292 0.010502959
#> 2005-11-04 -0.001127165 -0.003235750 -0.001198528 -0.000702757 0.011679558
#> 2005-11-07 -0.001795839  0.001310970  0.000360366  0.006205226 0.002709618
#> 2005-11-08  0.002103374  0.000539312  0.002327040  0.000329260 0.000346843
#>                     ALT
#> 2005-11-01 -0.002572971
#> 2005-11-02 -0.001141604
#> 2005-11-03  0.005007442
#> 2005-11-04  0.009482677
#> 2005-11-07  0.004723952
#> 2005-11-08  0.000853619
```
