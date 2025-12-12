# Class 'timeSeries' in package timeSeries

Class `"timeSeries"` in package timeSeries.

## Objects from the Class

The main functions for creating objects from class `"timeSeries"`
[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md)
and
[`as.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md).

Objects can also be created by calls of the form
`new("timeSeries", .Data, units, positions, format, FinCenter, recordIDs, title, documentation)`
but this is not recommended for routine work.

## Slots

The structure of the `"timeSeries"` objects should, in general, be
considered internal. The accessor functions to get and set the
components should be used to get and set values of the slots.

- `.Data`::

  Object of class `"matrix"` containing the data, one column for each
  variable.

- `units`::

  Object of class `"character"`, the unit (or variable, or column) names
  of the time series object.

- `positions`::

  Object of class `"numeric"`, the datetime stamps. If the time series
  doesn't have datetime stamps, then `positions` is of length zero.

- `format`::

  Object of class `"character"`, a datetime format (such as
  `"%Y-%m-%d"`). if there are no time stamps `"format"` is equal to
  `"counts"`.

- `FinCenter`::

  Object of class `"character"`, the financial center.

- `recordIDs`::

  Object of class `"data.frame"` \~~

- `title`::

  Object of class `"character"`, a title for printing.

- `documentation`::

  Object of class `"character"`, by default it is set to the current
  date.

## Extends

Class `"structure"`, from data part. Class `"vector"`, by class
"structure", distance 2, with explicit coerce.

## Methods

Below is a list of the methods that have `"timeSeries"` in their
signature. It can be useful for technical purposes, for example in
reporting bugs but most methods that need explanation are documented
with the corresponding functions and looking at their help pages is
recommended.

There are short explanations for methods for functions that are not
supposed to be called directly.

- \[:

  `signature(x = "timeSeries", i = "ANY", j = "index_timeSeries")`: ...

- \[:

  `signature(x = "timeSeries", i = "character", j = "character")`: ...

- \[:

  `signature(x = "timeSeries", i = "character", j = "index_timeSeries")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "character", j = "missing")`: ...

- \[:

  `signature(x = "timeSeries", i = "index_timeSeries", j = "character")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "index_timeSeries", j = "index_timeSeries")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "index_timeSeries", j = "missing")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "matrix", j = "missing")`: ...

- \[:

  `signature(x = "timeSeries", i = "missing", j = "character")`: ...

- \[:

  `signature(x = "timeSeries", i = "missing", j = "index_timeSeries")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "missing", j = "missing")`: ...

- \[:

  `signature(x = "timeSeries", i = "time_timeSeries", j = "ANY")`: ...

- \[:

  `signature(x = "timeSeries", i = "time_timeSeries", j = "character")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "time_timeSeries", j = "index_timeSeries")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "time_timeSeries", j = "missing")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "timeDate", j = "character")`: ...

- \[:

  `signature(x = "timeSeries", i = "timeDate", j = "index_timeSeries")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "timeDate", j = "missing")`: ...

- \[:

  `signature(x = "timeSeries", i = "timeSeries", j = "index_timeSeries")`:
  ...

- \[:

  `signature(x = "timeSeries", i = "timeSeries", j = "missing")`: ...

- \[\<-:

  `signature(x = "timeSeries", i = "character", j = "ANY")`: ...

- \[\<-:

  `signature(x = "timeSeries", i = "character", j = "missing")`: ...

- \[\<-:

  `signature(x = "timeSeries", i = "timeDate", j = "ANY")`: ...

- \[\<-:

  `signature(x = "timeSeries", i = "timeDate", j = "missing")`: ...

- \$:

  `signature(x = "timeSeries")`: ...

- \$\<-:

  `signature(x = "timeSeries", value = "ANY")`: ...

- \$\<-:

  `signature(x = "timeSeries", value = "factor")`: ...

- \$\<-:

  `signature(x = "timeSeries", value = "numeric")`: ...

- aggregate:

  `signature(x = "timeSeries")`: ...

- align:

  `signature(x = "timeSeries")`: ...

- apply:

  `signature(X = "timeSeries")`: ...

- as.data.frame:

  `signature(x = "timeSeries")`: ...

- as.list:

  `signature(x = "timeSeries")`: ...

- as.matrix:

  `signature(x = "timeSeries")`: ...

- as.ts:

  `signature(x = "timeSeries")`: ...

- attach:

  `signature(what = "timeSeries")`: ...

- cbind2:

  `signature(x = "ANY", y = "timeSeries")`: ...

- cbind2:

  `signature(x = "timeSeries", y = "ANY")`: ...

- cbind2:

  `signature(x = "timeSeries", y = "missing")`: ...

- cbind2:

  `signature(x = "timeSeries", y = "timeSeries")`: ...

- coerce:

  `signature(from = "ANY", to = "timeSeries")`

- coerce:

  `signature(from = "character", to = "timeSeries")`

- coerce:

  `signature(from = "data.frame", to = "timeSeries")`

- coerce:

  `signature(from = "timeSeries", to = "data.frame")`

- coerce:

  `signature(from = "timeSeries", to = "list")`:

- coerce:

  `signature(from = "timeSeries", to = "matrix")`

- coerce:

  `signature(from = "timeSeries", to = "ts")`:

- coerce:

  `signature(from = "ts", to = "timeSeries")`: `coerce` should not be
  called directly. Use `as(object, "target_class")` instead.

- colCummaxs:

  `signature(x = "timeSeries")`: ...

- colCummins:

  `signature(x = "timeSeries")`: ...

- colCumprods:

  `signature(x = "timeSeries")`: ...

- colCumreturns:

  `signature(x = "timeSeries")`: ...

- colCumsums:

  `signature(x = "timeSeries")`: ...

- colMeans:

  `signature(x = "timeSeries")`: ...

- colnames:

  `signature(x = "timeSeries")`: ...

- colnames\<-:

  `signature(x = "timeSeries")`: ...

- colSums:

  `signature(x = "timeSeries")`: ...

- comment:

  `signature(x = "timeSeries")`: ...

- comment\<-:

  `signature(x = "timeSeries")`: ...

- coredata:

  `signature(x = "timeSeries")`: ...

- coredata\<-:

  `signature(x = "timeSeries", value = "ANY")`: ...

- coredata\<-:

  `signature(x = "timeSeries", value = "matrix")`: ...

- cummax:

  `signature(x = "timeSeries")`: ...

- cummin:

  `signature(x = "timeSeries")`: ...

- cumprod:

  `signature(x = "timeSeries")`: ...

- cumsum:

  `signature(x = "timeSeries")`: ...

- diff:

  `signature(x = "timeSeries")`: ...

- dim:

  `signature(x = "timeSeries")`: ...

- dim\<-:

  `signature(x = "timeSeries")`: ...

- dimnames:

  `signature(x = "timeSeries")`: ...

- dimnames\<-:

  `signature(x = "timeSeries", value = "list")`: ...

- end:

  `signature(x = "timeSeries")`: ...

- filter:

  `signature(x = "timeSeries")`: ...

- finCenter:

  `signature(x = "timeSeries")`: ...

- finCenter\<-:

  `signature(x = "timeSeries")`: ...

- frequency:

  `signature(x = "timeSeries")`: ...

- getDataPart:

  `signature(object = "timeSeries")`: ...

- head:

  `signature(x = "timeSeries")`: ...

- initialize:

  `signature(.Object = "timeSeries")`:

  don't call `"initialize"`, call `new("timeSeries", ...)` instead. Even
  better, call `timeSeries`.

- is.na:

  `signature(x = "timeSeries")`: ...

- is.unsorted:

  `signature(x = "timeSeries")`: ...

- isDaily:

  `signature(x = "timeSeries")`: ...

- isMonthly:

  `signature(x = "timeSeries")`: ...

- isQuarterly:

  `signature(x = "timeSeries")`: ...

- isRegular:

  `signature(x = "timeSeries")`: ...

- lag:

  `signature(x = "timeSeries")`: ...

- lines:

  `signature(x = "timeSeries")`: ...

- median:

  `signature(x = "timeSeries")`: ...

- merge:

  `signature(x = "ANY", y = "timeSeries")`: ...

- merge:

  `signature(x = "matrix", y = "timeSeries")`: ...

- merge:

  `signature(x = "numeric", y = "timeSeries")`: ...

- merge:

  `signature(x = "timeSeries", y = "ANY")`: ...

- merge:

  `signature(x = "timeSeries", y = "matrix")`: ...

- merge:

  `signature(x = "timeSeries", y = "missing")`: ...

- merge:

  `signature(x = "timeSeries", y = "numeric")`: ...

- merge:

  `signature(x = "timeSeries", y = "timeSeries")`: ...

- na.contiguous:

  `signature(object = "timeSeries")`: ...

- na.omit:

  `signature(object = "timeSeries")`: ...

- names:

  `signature(x = "timeSeries")`: ...

- names\<-:

  `signature(x = "timeSeries")`: ...

- Ops:

  `signature(e1 = "array", e2 = "timeSeries")`: ...

- Ops:

  `signature(e1 = "timeSeries", e2 = "array")`: ...

- Ops:

  `signature(e1 = "timeSeries", e2 = "timeSeries")`: ...

- Ops:

  `signature(e1 = "timeSeries", e2 = "ts")`: ...

- Ops:

  `signature(e1 = "timeSeries", e2 = "vector")`: ...

- Ops:

  `signature(e1 = "ts", e2 = "timeSeries")`: ...

- Ops:

  `signature(e1 = "vector", e2 = "timeSeries")`: ...

- outlier:

  `signature(x = "timeSeries")`: ...

- plot:

  `signature(x = "timeSeries")`: ...

- points:

  `signature(x = "timeSeries")`: ...

- print:

  `signature(x = "timeSeries")`: ...

- quantile:

  `signature(x = "timeSeries")`: ...

- rank:

  `signature(x = "timeSeries")`: ...

- rbind2:

  `signature(x = "ANY", y = "timeSeries")`: ...

- rbind2:

  `signature(x = "timeSeries", y = "ANY")`: ...

- rbind2:

  `signature(x = "timeSeries", y = "missing")`: ...

- rbind2:

  `signature(x = "timeSeries", y = "timeSeries")`: ...

- returns:

  `signature(x = "timeSeries")`: ...

- rev:

  `signature(x = "timeSeries")`: ...

- rowCumsums:

  `signature(x = "timeSeries")`: ...

- rownames:

  `signature(x = "timeSeries")`: ...

- rownames\<-:

  `signature(x = "timeSeries", value = "ANY")`: ...

- rownames\<-:

  `signature(x = "timeSeries", value = "timeDate")`: ...

- sample:

  `signature(x = "timeSeries")`: ...

- scale:

  `signature(x = "timeSeries")`: ...

- series:

  `signature(x = "timeSeries")`: ...

- series\<-:

  `signature(x = "timeSeries", value = "ANY")`: ...

- series\<-:

  `signature(x = "timeSeries", value = "matrix")`: ...

- setDataPart:

  `signature(object = "timeSeries")`: ...

- show:

  `signature(object = "timeSeries")`: ...

- sort:

  `signature(x = "timeSeries")`: ...

- start:

  `signature(x = "timeSeries")`: ...

- str:

  `signature(object = "timeSeries")`: ...

- t:

  `signature(x = "timeSeries")`: ...

- tail:

  `signature(x = "timeSeries")`: ...

- time:

  `signature(x = "timeSeries")`: ...

- window:

  `signature(x = "timeSeries")`: ...

## See also

[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md)
and
[`as.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
for creating and converting to `"timeSeries"`,

[`readSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-readSeries.md)
for importing from a text file,

[`dummyDailySeries`](https://geobosh.github.io/timeSeriesDoc/reference/fin-dummy.md)
for creation of dummy daily and monthly time series,

[`as.matrix`](https://rdrr.io/r/base/matrix.html),
[`time`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotTime.md),
[`finCenter`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotFinCenter.md),
[`getUnits`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotUnits.md),
[`dim`](https://rdrr.io/r/base/dim.html),
[`start`](https://geobosh.github.io/timeSeriesDoc/reference/base-start.md),
etc., for accessing properties of the time series.

## Examples

``` r
## see the help page for timeSeries()
showClass("timeSeries")
#> Class "timeSeries" [package "timeSeries"]
#> 
#> Slots:
#>                                                                             
#> Name:          .Data         units     positions        format     FinCenter
#> Class:        matrix     character       numeric     character     character
#>                                                 
#> Name:      recordIDs         title documentation
#> Class:    data.frame     character     character
#> 
#> Extends: 
#> Class "structure", from data part
#> Class "vector", by class "structure", distance 2, with explicit coerce
```
