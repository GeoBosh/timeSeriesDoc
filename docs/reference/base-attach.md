# Attach a 'timeSeries' to the search path

Attaches a `"timeSeries"` object to the search path.

## Usage

``` r
# S4 method for class 'timeSeries'
attach(what, pos = 2, name = deparse(substitute(what)), 
    warn.conflicts = TRUE)
```

## Note

The function `detach` from the `base` package can be used to detach the
attached objects.

## Arguments

- name:

  alternative way to specify the database to be attached. See for
  details
  [`help(attach, package = base)`](https://rdrr.io/r/base/attach.html).

- pos:

  an integer specifying position in
  [`search()`](https://rdrr.io/r/base/search.html) where to attach the
  database. See for details
  [`help(attach, package = base)`](https://rdrr.io/r/base/attach.html).

- warn.conflicts:

  a logical value. If `TRUE`, warnings are printed about conflicts from
  attaching the database, unless that database contains an object
  `.conflicts.OK`. A conflict is a function masking a function, or a
  non-function masking a non-function. See for details
  [`help(attach, package = base)`](https://rdrr.io/r/base/attach.html).

- what:

  database to be attached. This may currently be a `"timeSeries"`
  object, a data.frame, a list, an R data file created with `save`,
  `NULL`, or an environment. See for details
  [`help(attach, package = base)`](https://rdrr.io/r/base/attach.html).

## Value

the environment, invisibly, with a `name` attribute

## Examples

``` r
## Load Microsoft Data Set - 
   x <- MSFT[1:10, ]
   colnames(x)
#> [1] "Open"   "High"   "Low"    "Close"  "Volume"
   
## Attach the Series and Compute the Range - 
   attach(x)
   range <- High - Low
   range
#>  [1] 3.7500 1.2500 2.6875 2.5625 3.3125 2.0625 2.0000 2.0000 2.7500 1.7500
   
## Convert Vector to a \code{"timeSeries"} Object -
   timeSeries(data=range, charvec=time(x), units="Range")
#> GMT 
#>             Range
#> 2000-09-27 3.7500
#> 2000-09-28 1.2500
#> 2000-09-29 2.6875
#> 2000-10-02 2.5625
#> 2000-10-03 3.3125
#> 2000-10-04 2.0625
#> 2000-10-05 2.0000
#> 2000-10-06 2.0000
#> 2000-10-09 2.7500
#> 2000-10-10 1.7500
   
## Detach the series from the search path -
   detach("x")
   ans <- try(High, silent=TRUE)
   cat(ans[1])
#> Error in eval(expr, envir) : object 'High' not found
```
