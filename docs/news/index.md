# Changelog

## timeSeries 4052.112

- removed deprecated functions `interpNA` and `substituteNA`. Use
  `na.omit` instead, see
  [`?na.omit.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/stats-na.omit.md)
  for details. (The deprecated `removeNA` is kept for now, since it is
  used in a package.)

- removed a number of unexported deprecated functions starting with a
  ‘.’, which had exported variants without the starting ‘.’.

- removed the unnecessary tabular environment in
  ‘timeSeries-deprecated.Rd’.

- corrected minor typo’s (e.g., changed a `getRmetricsOption` to
  `getRmetricsOptions` in an error message).

## timeSeries 4041.111

CRAN release: 2024-09-22

- now ‘timeSeries’ depends on ‘timeDate’ version 4041.110 or later. If
  you have an older version of ‘timeSeries’ and it stops working after
  updating ‘timeDate’, install the latest version of ‘timeSeries’.

  The incompatibility was necessitated by the need to fix a bug.

## timeSeries 4041.110

CRAN release: 2024-09-16

- this is a technical update, there are no user visible changes.

- There was an explicit call to
  [`timeDate::months`](https://geobosh.github.io/timeDateDoc/reference/calendar-julian.html)
  in the code, but the upcoming v4041.110 of timeDate doesn’t export
  `months` anymore (in package code call `stats::months` or import
  `months` from `stats` and use `months` without the package prefix).

## timeSeries 4032.109

CRAN release: 2024-01-14

- deprecated function `returnSeries` is now defunct, use `returns`
  instead.

- a number of generic functions from base R now get only S3 methods for
  ‘timeSeries’ objects. Previously they were turned into S4 generics
  with S4 methods.

- streamlined `"timeSeries"` methods for a number of functions. Left
  only S3 methods or only S4 methods were suitable.

- consolidated the NAMESPACE.

## timeSeries 4032.108

CRAN release: 2023-12-19

- fixed ‘Lost braces; missing escapes or markup?’ NOTE from CRAN.

## timeSeries 4031.107

CRAN release: 2023-08-26

- refactored the ‘timeSeries’ methods for `head` and `tail`.

- fixed a bug in the ‘timeSeries’ method for
  [`stats::na.contiguous`](https://rdrr.io/r/stats/na.contiguous.html),
  which caused the wrong stretch to be returned in the case of tied
  longest stretches one of whom starts at the beginning of the series.
  Similar bug was present in
  [`stats::na.contiguous.default`](https://rdrr.io/r/stats/na.contiguous.html),
  see my bug report to R-devel from 2023-06-02 and the discussion there
  (<https://stat.ethz.ch/pipermail/r-devel/2023-June/082642.html>)

- removed deprecated functions `spreadSeries`, `midquoteSeries`, and
  `durationSeries`. Use `spreads`, `midquotes`, and `durations`,
  respectively.

- removed deprecated function `colStdevs`, use
  [`colSds()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  instead.

- removed deprecated function `.description`, use
  [`description()`](https://geobosh.github.io/timeSeriesDoc/reference/utils-description.md)
  instead.

- removed deprecated ‘timeSeries’ method for function
  [`cut()`](https://rdrr.io/r/base/cut.html), use
  [`window()`](https://geobosh.github.io/timeSeriesDoc/reference/stats-window.md)
  instead. The method was not compatible with the generic function
  [`cut()`](https://rdrr.io/r/base/cut.html). Now applying `cut(x)` on a
  ‘timeSeries’ object `x` will work on the underlying time series data.

- replaced the S4 methods for
  [`zoo::coredata`](https://rdrr.io/pkg/zoo/man/coredata.html) and
  [`zoo::'coredata<-'`](https://rdrr.io/pkg/zoo/man/coredata.html). The
  ones for
  [`zoo::'coredata<-'`](https://rdrr.io/pkg/zoo/man/coredata.html) were
  not working at all, since
  [`zoo::'coredata<-'`](https://rdrr.io/pkg/zoo/man/coredata.html) is an
  S3 generic and the methods dispatch on two arguments. It is also a
  mistery why the methods for the unexported S4 generics in ‘timeSeries’
  were associated with the corresponding ‘zoo’ generics.

  If `zoo` is not attached, the calls need to be prefixed with `zoo::`
  or, alternatively, since the new methods are exported, they can be
  called directly as
  [`coredata.timeSeries()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotSeries.md)
  and \``coredata.'timeSeries<-'() <- value`.

- added a default method for `time<-` to improve its interaction with
  ‘zoo’.

- added ‘zoo’ to ‘Suggests:’.

- removed the deprecated `dummySeries`, use `dummyMonthlySeries`
  instead.

- added argument `FUN` to the `timeSeries` method for `na.omit` to allow
  it to compute replacement values using functions, such as `mean`,
  `median`, or user defined.

- formally deprecated `removeNA`, `interpNA`, and `substituteNA`. These
  had been informally deprecated in the documentation for a long time.

- the help page for `orderStatistics` erroneously claimed that the input
  should be an univariate `timeSeries` object, while it is explicitly
  written to cover the multivariate case.

- moved package ‘methods’ back to ‘Depends’ to avoid subtle problems
  when ‘methods’ is loaded but not attached. For example, it seems that
  ‘Math’ methods for ‘structure’ are not seen for `cummin` and other
  `cumXXX` functions, when called on time series objects (the other math
  functions work ok).

- `cumsum`, `cumprod`, `cummin`, and `cummax` now work on the columns of
  the ‘timeSeries’ object and keep its class and other attributes. This
  is a breaking change since previously the return value was numeric
  vector, the result of applying the base R functions to the data part
  of the object. This was not particularly useful, especilly for
  multivariate time series. With this change all functions from the S4
  `Math` group return ‘timeSeries’ when their argument is ‘timeSeries’
  object.

- stopped exporting some internal functions that were accidentally used
  by other packages (after those packages were updated on CRAN).

- Numerous improvements to the documentation and further changes in the
  code.

## timeSeries 4030.106

CRAN release: 2023-05-25

- removed UTF8 characters from NAMESPACE (fixes CRAN warning to that
  effect).

## timeSeries 4021.105

CRAN release: 2022-10-15

- updated and significantly improved the documentation.

- class `timeSeries` now has a dedicated summary method. Previously it
  was falling back to the method for matrices.

- `colCumsums`, `colCummaxs`, `colCummins`, and `colCumprods` no longer
  throw error for `timeSeries` objects when called with `na.rm = TRUE`.
  Fixes bug \#2121 reported by Shane Haas.

- corrected USDCHF dataset. The year information was wrong (the data
  started from year 8295). The bug had been introduced in version
  2100.84 when the dataset file was converted from a `usdchf.csv` to
  `USDCHF.rda`. `USDCHF@documentation` contains a short note about this
  change. Also changed the FinCenter to Zurich (neither the
  documentation nor the csv file contain FinCenter information).

- the original source file `msft.dat.csv` of the `MSFT` data is included
  now as `inst/extdata/msft.csv` (note the different name). The file had
  been removed in v2100.84. Note that there is a file \``msft.dat.csv`
  in `test/` but it is a modified and abbreviated version of the
  original file.

- `dummySeries` has been renamed to the more expressive
  `dummyMonthlySeries`. The old name is still available but is
  deprecated.

- The functions `returnSeries` and `getReturns` are no longer exported
  and will be removed in the near future. They are synonyms for the
  function `returns` and their use was discouraged for many years. Just
  use `returns`.

- ‘timeSeries’ method for function
  [`cut()`](https://rdrr.io/r/base/cut.html) is now formally deprecated.
  Use `window` instead.

- deprecated function `seriesData` is now defunct. Use
  [`as.matrix()`](https://rdrr.io/r/base/matrix.html) instead.

- deprecated function `seriesPositions` is now defunct. Use
  [`time()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotTime.md)
  instead.

- deprecated function `newPositions<-` is now defunct. Use `time<-`
  instead.

- deprecated function `colAvgs` is now defunct. Use
  [`colMeans()`](https://rdrr.io/r/base/colSums.html) instead.

- deprecated function `colStdevs` is now defunct. Use
  [`colSds()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  instead.

### Technical changes

- stopped exporting (almost) all functions whose names start with a ‘.’.
  Historically, the package was exporting all functions, including those
  starting with a ‘.’. This should be of no concern for users since
  these functions were not documented but the developers of some
  Rmetrics packages where using such functions.

- the additional arguments of the S3 `timeSeries` method for
  [`diff()`](https://geobosh.github.io/timeSeriesDoc/reference/base-diff.md)
  are now in its signature, which previously was `diff(x, ...)`. An
  intermediate function, `.diff.timeSeries`, was eliminated in the
  process.

- the bodies of the methods of `series<-` and `coredata<-` for signature
  `"matrix"` or value were identical. Now the body is a separate,
  unexported function, which is used as the definition of both of these
  methods.

- eliminated `.merge.timeSeries` and other redundancy in the
  implementation of the `c("timeSeries", "timeSeries")` method.

- eliminated `.rev.timeSeries` in the definition of the `rev` method.

- eliminated `.scale.timeSeries` in the definition of the `scale`
  timeSeries method.

- same as above for `.sort.timeSeries`.

- eliminated `.start.timeSeries`and the redundancy in the implementation
  of the `timeSeries` method.

- eliminated `.end.timeSeries` and the redundancy in the implementation
  of the `timeSeries` method.

- the function `.applySeries` is now defunct. It was obsoleted long time
  ago and was exported for historical reasons only. Use
  [`applySeries()`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)
  instead.

## timeSeries 4021.104

CRAN release: 2022-07-17

- new maintainer: Georgi Boshnakov.

- moved package `methods` to `Imports`.

- fixed CRAN NOTE `Escaped LaTeX specials: \_ \_` in `methods-plot.Rd`.

## timeSeries 3062.100 and older

CRAN release: 2020-01-24

See file `ChangeLog`.
