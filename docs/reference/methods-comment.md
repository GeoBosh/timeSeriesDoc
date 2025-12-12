# Get and set comments for 'timeSeries' objects

Get or assign new comment to a `timeSeries` object.

## Usage

``` r
# S4 method for class 'timeSeries'
comment(x)
# S4 method for class 'timeSeries'
comment(x) <- value
```

## Arguments

- x:

  a `timeSeries` object.

- value:

  a character vector, the comment.

## Details

Objects from class `"timeSeries"` have a slot for documentation. These
functions get and change its contents.

## Examples

``` r
## Get description from a 'timeSeries' -
   comment(LPP2005REC)
#> [1] "Thu Aug 27 17:27:15 2009"
   
## Add User to comment -
   comment(LPP2005REC) <- paste(comment(LPP2005REC), "by User Rmetrics")
   comment(LPP2005REC)
#> [1] "Thu Aug 27 17:27:15 2009 by User Rmetrics"
```
