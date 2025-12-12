# DataPart,timeSeries-method

Utilities called to implement object@.Data of `timeSeries` objects.

## Examples

``` r
## Load Microsoft Data -
   X <- MSFT[1:10, 1:4]
   
## Get Data Part - 
   DATA <- getDataPart(X)
   class(DATA)
#> [1] "matrix" "array" 
```
