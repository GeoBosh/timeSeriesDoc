# Get and set optional attributes of a 'timeSeries'

Extracts or assigns optional attributes from or to a `"timeSeries"`
object.

## Usage

``` r
getAttributes(obj)         
setAttributes(obj) <- value
```

## Arguments

- obj:

  a `timeSeries` object whose optional attributes are to be accessed.

- value:

  an object, the new value of the attribute, or NULL to remove the
  attribute.

## Details

Each `timeSeries` object is documented. By default a time series object
holds in the documentation slot a string with creation time and the user
who has defined it. But this is not all. Optionally the whole creation
process and history can be recorded. For this the `@documentation` slot
may have an optional `"Attributes"` element. This attribute is tracked
over the whole life time of the object whenever the time series is
changed. Whenever you like to be informed about the optional attributes,
or you like to recover them you can dot it, and evenmore, whenever you
like to add information as an addiitonal attribute you can also do it.

The two functions `getAttributes` and `setAttributes` provide access to
and allow to modify the optional attributes of a `timeSeries` object.

## Examples

``` r
## Create an artificial 'timeSeries' Object - 
   tS <- dummyMonthlySeries()
   tS
#> GMT 
#>                   TS.1       TS.2
#> 2025-01-01 0.113703411 0.28273358
#> 2025-02-01 0.622299405 0.92343348
#> 2025-03-01 0.609274733 0.29231584
#> 2025-04-01 0.623379442 0.83729563
#> 2025-05-01 0.860915384 0.28622328
#> 2025-06-01 0.640310605 0.26682078
#> 2025-07-01 0.009495756 0.18672279
#> 2025-08-01 0.232550506 0.23222591
#> 2025-09-01 0.666083758 0.31661245
#> 2025-10-01 0.514251141 0.30269337
#> 2025-11-01 0.693591292 0.15904600
#> 2025-12-01 0.544974836 0.03999592

## Get Optional Attributes -
   getAttributes(tS)
#> NULL
   tS@documentation
#> [1] "Fri Dec 12 16:28:27 2025"
   
## Set a new Optional Attribute -
   setAttributes(tS) <- list(what="A dummy Series")
   tS
#> GMT 
#>                   TS.1       TS.2
#> 2025-01-01 0.113703411 0.28273358
#> 2025-02-01 0.622299405 0.92343348
#> 2025-03-01 0.609274733 0.29231584
#> 2025-04-01 0.623379442 0.83729563
#> 2025-05-01 0.860915384 0.28622328
#> 2025-06-01 0.640310605 0.26682078
#> 2025-07-01 0.009495756 0.18672279
#> 2025-08-01 0.232550506 0.23222591
#> 2025-09-01 0.666083758 0.31661245
#> 2025-10-01 0.514251141 0.30269337
#> 2025-11-01 0.693591292 0.15904600
#> 2025-12-01 0.544974836 0.03999592
   getAttributes(tS)
#> $what
#> $what[[1]]
#> [1] "A dummy Series"
#> 
#> 
   tS@documentation
#> [1] "Fri Dec 12 16:28:27 2025"
#> attr(,"Attributes")
#> attr(,"Attributes")$what
#> attr(,"Attributes")$what[[1]]
#> [1] "A dummy Series"
#> 
#> 
```
