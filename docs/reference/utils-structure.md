# Display the structure of 'timeSeries' objects

Compactly display the structure of a `"timeSeries"` object.

## Usage

``` r
# S3 method for class 'timeSeries'
str(object, ...)
```

## Arguments

- object:

  an object of class `timeSeries`.

- ...:

  arguments passed to other methods.

## Value

`NULL`, invisibly. The function is called for its side effect of
printing a compact representation of the structure of the `"timeSeries"`
object.

## Examples

``` r
## Load Microsoft Data Set
data(MSFT)
X <- MSFT[1:12, 1:4]
colnames(X) <- abbreviate(colnames(X), 4)
    
## Display Structure
str(X)
#> Time Series:          
#>  Name:               X
#> Data Matrix:        
#>  Dimension:          12 4
#>  Column Names:       Open High Low Clos
#>  Row Names:          2000-09-27  ...  2000-10-12
#> Positions:          
#>  Start:              2000-09-27
#>  End:                2000-10-12
#> With:               
#>  Format:             %Y-%m-%d
#>  FinCenter:          GMT
#>  Units:              Open High Low Clos
#>  Title:              Time Series Object
#>  Documentation:      
```
