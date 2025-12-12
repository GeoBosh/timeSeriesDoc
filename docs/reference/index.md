# Package index

## Overview of package timeSeries

- [`timeSeries-package`](https://geobosh.github.io/timeSeriesDoc/reference/00timeSeries-package.md)
  : Utilities and tools package
- [`TimeSeriesData`](https://geobosh.github.io/timeSeriesDoc/reference/data-examples.md)
  [`LPP2005REC`](https://geobosh.github.io/timeSeriesDoc/reference/data-examples.md)
  [`MSFT`](https://geobosh.github.io/timeSeriesDoc/reference/data-examples.md)
  [`USDCHF`](https://geobosh.github.io/timeSeriesDoc/reference/data-examples.md)
  : Time series data sets

## Create ‘timeSeries’ objects

- [`timeSeries()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md)
  : Create objects from class 'timeSeries'
- [`readSeries()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-readSeries.md)
  : Read a 'timeSeries' from a text file
- [`dummyDailySeries()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-dummy.md)
  [`dummyMonthlySeries()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-dummy.md)
  : Create dummy time series
- [`as.timeSeries()`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
  [`as.ts(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
  [`as.matrix(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
  [`as.data.frame(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
  [`as.list(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md)
  : Convert objects to/from class 'timeSeries'

## Explore ‘timeSeries’ objects

- [`plot(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-plot.md)
  [`lines(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-plot.md)
  [`points(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-plot.md)
  [`pretty(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-plot.md)
  : Plot 'timeSeries' objects
- [`show(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-show.md)
  [`print(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-show.md)
  : Print 'timeSeries' objects
- [`str(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/utils-structure.md)
  : Display the structure of 'timeSeries' objects
- [`is.timeSeries()`](https://geobosh.github.io/timeSeriesDoc/reference/methods-is.md)
  [`is.signalSeries()`](https://geobosh.github.io/timeSeriesDoc/reference/methods-is.md)
  : Check if an object is from class 'timeSeries'
- [`isUnivariate()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isUnivariate.md)
  [`isMultivariate()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isUnivariate.md)
  : Checks if a time series is univariate
- [`isDaily(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)
  [`isMonthly(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)
  [`isQuarterly(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)
  [`isRegular(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)
  [`frequency(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)
  : Checks if a time series is regular
- [`na.contiguous(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-na.contiguous.md)
  [`is.na(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-na.contiguous.md)
  : Find longest contiguous stretch of non-NAs or check for NAs
- [`sort(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-sort.md)
  [`is.unsorted(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-sort.md)
  : Sort a 'timeSeries' by time stamps

## Subset ‘timeSeries’ objects

There are ‘timeSeries’ methods for subsetting operators, like ‘\[’ and
‘\[\<-’, as well as functions and methods which broadly perform some
kind of subsetting.

- [`window(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-window.md)
  : Methods for 'window' in package 'timeSeries'
- [`head(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-subsetting.md)
  [`tail(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-subsetting.md)
  [`outlier()`](https://geobosh.github.io/timeSeriesDoc/reference/base-subsetting.md)
  : Subsetting time series
- [`na.contiguous(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-na.contiguous.md)
  [`is.na(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-na.contiguous.md)
  : Find longest contiguous stretch of non-NAs or check for NAs
- [`na.omit(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-na.omit.md)
  : Handle missing values in 'timeSeries' objects
- [`removeNA()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-deprecated.md)
  : Deprecated functions in 'timeSeries' package
- [`endOfPeriodSeries()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-periodical.md)
  [`endOfPeriodStats()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-periodical.md)
  [`endOfPeriodBenchmarks()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-periodical.md)
  : End-of-Period series, stats, and benchmarks

## Aggregate and smooth ‘timeSeries’ objects

- [`filter(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-filter.md)
  : Linear filtering on a time series
- [`smoothLowess()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md)
  [`smoothSpline()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md)
  [`smoothSupsmu()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md)
  : Smooths time series objects
- [`aggregate(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-aggregate.md)
  : Aggregate time series
- [`align(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/fin-align.md)
  [`alignDailySeries()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-align.md)
  [`daily2monthly()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-align.md)
  [`daily2weekly()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-align.md)
  : Align a 'timeSeries' object to equidistant time stamps
- [`apply(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)
  [`fapply()`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)
  [`applySeries()`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)
  [`rollDailySeries()`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)
  : Apply functions over time windows
- [`rollMonthlyWindows()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-monthly.md)
  [`rollMonthlySeries()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-monthly.md)
  [`countMonthlyRecords()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-monthly.md)
  : Special monthly series

## Manipulate ‘timeSeries’ objects

- [`series()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotSeries.md)
  [`` `series<-`() ``](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotSeries.md)
  : Get and set the data component of a 'timeSeries'
- [`finCenter(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotFinCenter.md)
  [`` `finCenter<-`( ``*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotFinCenter.md)
  [`getFinCenter()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotFinCenter.md)
  [`` `setFinCenter<-`() ``](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotFinCenter.md)
  : Get and set Financial center of a 'timeSeries'
- [`time(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotTime.md)
  [`` `time<-`( ``*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotTime.md)
  [`getTime()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotTime.md)
  [`` `setTime<-`() ``](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotTime.md)
  : Get and set time stamps of a 'timeSeries'
- [`getUnits()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotUnits.md)
  [`` `setUnits<-`() ``](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotUnits.md)
  : Get and set unit names of a 'timeSeries'
- [`start(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-start.md)
  [`end(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-start.md)
  : Start and end of a 'timeSeries'
- [`getAttributes()`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotDocumentation.md)
  [`` `setAttributes<-`() ``](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotDocumentation.md)
  : Get and set optional attributes of a 'timeSeries'
- [`comment(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-comment.md)
  [`` `comment<-`( ``*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-comment.md)
  : Get and set comments for 'timeSeries' objects
- [`orderColnames()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)
  [`sortColnames()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)
  [`sampleColnames()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)
  [`statsColnames()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)
  [`pcaColnames()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)
  [`hclustColnames()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)
  : Reorder column names of a time series

## Transform ‘timeSeries’ objects

- [`scale(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-scale.md)
  : Center and scale 'timeSeries' objects
- [`diff(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-diff.md)
  : Difference a 'timeSeries' object
- [`colCumsums(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)
  [`colCummaxs(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)
  [`colCummins(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)
  [`colCumprods(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)
  [`colCumreturns(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)
  : Cumulated column statistics
- [`rowCumsums(`*`<ANY>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rowCumsums.md)
  [`rowCumsums(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rowCumsums.md)
  : Cumulative row statistics
- [`lag(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/stats-lag.md)
  : Lag a 'timeSeries' object
- [`sort(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-sort.md)
  [`is.unsorted(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-sort.md)
  : Sort a 'timeSeries' by time stamps
- [`rev(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-rev.md)
  : Reverse a 'timeSeries'
- [`runlengths()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-runlengths.md)
  : Runlengths of a time series
- [`durations()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-durations.md)
  : Durations from a 'timeSeries'
- [`rank(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-rank.md)
  : Sample ranks of a time series
- [`sample(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-sample.md)
  : Resample 'timeSeries' objects
- [`Ops(`*`<timeSeries>`*`,`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`Math(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`Math2(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`quantile(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`median(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  : Mathematical operations on 'timeSeries'

## Financial computations on ‘timeSeries’ objects

- [`returns()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md)
  [`returns0()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md)
  : Financial returns
- [`cumulated()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-cumulated.md)
  : Cumulated time series from returns
- [`drawdowns()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md)
  [`drawdownsStats()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md)
  : Calculations of drawdowns
- [`splits()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-splits.md)
  : splits
- [`spreads()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md)
  [`midquotes()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md)
  : Spreads and mid quotes
- [`index2wealth()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-wealth.md)
  : Conversion of an index to wealth

## Compute statistics on timeSeries objects

- [`sd-methods`](https://geobosh.github.io/timeSeriesDoc/reference/methods-stats.md)
  [`var-methods`](https://geobosh.github.io/timeSeriesDoc/reference/methods-stats.md)
  [`cov-methods`](https://geobosh.github.io/timeSeriesDoc/reference/methods-stats.md)
  [`cor-methods`](https://geobosh.github.io/timeSeriesDoc/reference/methods-stats.md)
  : Base R functions applied to 'timeSeries' objects
- [`colStats()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colSds()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colVars()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colSkewness()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colKurtosis()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colMaxs()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colMins()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colProds()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  [`colQuantiles()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)
  : Column statistics
- [`turns()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-turnpoints.md)
  [`turnsStats()`](https://geobosh.github.io/timeSeriesDoc/reference/fin-turnpoints.md)
  : Turning points of a time series
- [`orderStatistics()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderStatistics.md)
  : Order statistics
- [`rollStats()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)
  [`rollMean()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)
  [`rollMin()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)
  [`rollMax()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)
  [`rollMedian()`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)
  : Rolling statistics

## Combine time series

- [`cbind(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-cbind.md)
  [`rbind(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-cbind.md)
  [`cbind2(`*`<timeSeries>`*`,`*`<ANY>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-cbind.md)
  [`rbind2(`*`<timeSeries>`*`,`*`<ANY>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-cbind.md)
  : Bind 'timeSeries' objects by column or row
- [`merge()`](https://geobosh.github.io/timeSeriesDoc/reference/base-merge.md)
  : Merge 'timeSeries' objects

## Mathematical operations on ‘timeSeries’

- [`Ops(`*`<timeSeries>`*`,`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`Math(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`Math2(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`quantile(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  [`median(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)
  : Mathematical operations on 'timeSeries'
- [`t(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-t.md)
  : Transpose 'timeSeries' objects

## Other

- [`timeSeries-class`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-class.md)
  [`initialize,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-class.md)
  : Class 'timeSeries' in package timeSeries
- [`dim,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`dim<-,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`dimnames,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`dimnames<-,timeSeries,list-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`colnames<-,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`colnames,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`rownames,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`rownames<-,timeSeries,timeDate-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`rownames<-,timeSeries,ANY-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`names,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  [`names<-,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)
  : Dimension and their names for 'timeSeries' objects
- [`getDataPart,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-getDataPart.md)
  [`setDataPart,timeSeries-method`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-getDataPart.md)
  : DataPart,timeSeries-method
- [`description()`](https://geobosh.github.io/timeSeriesDoc/reference/utils-description.md)
  : Creates date and user information
- [`attach(`*`<timeSeries>`*`)`](https://geobosh.github.io/timeSeriesDoc/reference/base-attach.md)
  : Attach a 'timeSeries' to the search path
- [`.colorwheelPalette()`](https://geobosh.github.io/timeSeriesDoc/reference/internals.md)
  : Exported internal functions
