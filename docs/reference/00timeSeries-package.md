# Utilities and tools package

Package timeSeries is part of the Rmetrics suit of R packages. It
provides a class, `timeSeries`, particularly aimed at analysis of
financial data, along with many methods, functions, and utilities for
statistical and financial computations on time series.

## Author

Diethelm Wuertz \[aut\] (original code), Tobias Setz \[aut\], Yohan
Chalabi \[aut\], Martin Maechler \[ctb\]
(\<https://orcid.org/0000-0002-8685-9910\>), Georgi N. Boshnakov \[cre,
aut\]

Maintainer: Georgi N. Boshnakov \<georgi.boshnakov@manchester.ac.uk\>

## Details

The following sections have not been updated for some time.

## timeSeries - S4 'timeSeries' Class

|                                                                                                  |                                       |
|--------------------------------------------------------------------------------------------------|---------------------------------------|
| [`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md)                  | Creates a `"timeSeries"` from scratch |
| [`series`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotSeries.md), coredata | Extracts the data                     |
| [`getUnits`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotUnits.md)          | Extracts the time serie units         |
| [`time`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotTime.md)               | Extracts the positions of timestamps  |
| `x@format`                                                                                       | Extracts the format of the timestamp  |
| [`finCenter`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-slotFinCenter.md)     | Extracts the financial center         |
| `x@recordIDs`                                                                                    | Extracts the record IDs               |
| `x@title`                                                                                        | Extracts the title                    |
| `x@documentation`                                                                                | Extracts the documentation            |

## Base Time Series Functions

|                                                                              |                                                  |
|------------------------------------------------------------------------------|--------------------------------------------------|
| [`apply`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)   | Applies a function to blocks of a `"timeSeries"` |
| [`cbind`](https://geobosh.github.io/timeSeriesDoc/reference/base-cbind.md)   | Combines columns of two `"timeSeries"` objects   |
| [`rbind`](https://geobosh.github.io/timeSeriesDoc/reference/base-cbind.md)   | Combines rows of two `"timeSeries"` objects      |
| [`diff`](https://geobosh.github.io/timeSeriesDoc/reference/base-diff.md)     | Returns differences of a `"timeSeries"` object   |
| [`dim`](https://geobosh.github.io/timeSeriesDoc/reference/base-dim.md)       | returns dimensions of a `"timeSeries"` object    |
| [`merge`](https://geobosh.github.io/timeSeriesDoc/reference/base-merge.md)   | Merges two `"timeSeries"` objects                |
| [`rank`](https://geobosh.github.io/timeSeriesDoc/reference/base-rank.md)     | Returns sample ranks of a `"timeSeries"` object  |
| [`rev`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)     | Reverts a `"timeSeries"` object                  |
| [`sample`](https://geobosh.github.io/timeSeriesDoc/reference/base-sample.md) | Resamples a `"timeSeries"` object                |
| [`scale`](https://geobosh.github.io/timeSeriesDoc/reference/base-scale.md)   | Scales a `"timeSeries"` object                   |
| [`sort`](https://geobosh.github.io/timeSeriesDoc/reference/base-sort.md)     | Sorts a `"timeSeries"` object                    |
| [`start`](https://geobosh.github.io/timeSeriesDoc/reference/base-start.md)   | Returns start date/time of a `"timeSeries"`      |
| [`end`](https://geobosh.github.io/timeSeriesDoc/reference/base-start.md)     | Returns end date/time of a `"timeSeries"`        |
| [`end`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)     | Returns end date/time of a `"timeSeries"`        |
| [`t`](https://geobosh.github.io/timeSeriesDoc/reference/base-t.md)           | Returns the transpose of a `"timeSeries"` object |
| [`attach`](https://geobosh.github.io/timeSeriesDoc/reference/base-attach.md) | Attaches a `"timeSeries"` to the search path     |

## Subsetting 'timeSeries' Objects

|                                                                                 |                                                |
|---------------------------------------------------------------------------------|------------------------------------------------|
| `[`                                                                             | Subsets a `"timeSeries"` object                |
| `[<-`                                                                           | Assigns values to a subset                     |
| `$`                                                                             | Subsets a `"timeSeries"` by column names       |
| `$<-`                                                                           | Replaces subset by column names                |
| [`head`](https://geobosh.github.io/timeSeriesDoc/reference/base-subsetting.md)  | Returns the head of a `"timeSeries"`           |
| [`tail`](https://geobosh.github.io/timeSeriesDoc/reference/base-subsetting.md)  | Returns the tail of a time Series              |
| [`na.omit`](https://geobosh.github.io/timeSeriesDoc/reference/stats-na.omit.md) | Handles NAs in a `"timeSeries"` object         |
| `removeNA`                                                                      | removes NAs from a matrix object               |
| `substituteNA`                                                                  | substitutes NAs by zero, column mean or median |
| `interpNA`                                                                      | interpolates NAs using R's "approx" function   |

## Mathematical Operation

|                                                                                    |                                                           |
|------------------------------------------------------------------------------------|-----------------------------------------------------------|
| [`Ops`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)      | S4: Arith method for a `"timeSeries"` object              |
| [`Math`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)     | S4: Math method for a `"timeSeries"` object               |
| [`Math2`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md)    | S4: Maths method for a `"timeSeries"` object              |
| `abs`                                                                              | Returns absolute values of a `"timeSeries"` object        |
| `sqrt`                                                                             | Returns square root of a `"timeSeries"` object            |
| `exp`                                                                              | Returns the exponential values of a `"timeSeries"` object |
| `log`                                                                              | Returns the logarithm of a `"timeSeries"` object          |
| `sign`                                                                             | Returns the signs of a `"timeSeries"` object              |
| [`diff`](https://geobosh.github.io/timeSeriesDoc/reference/base-diff.md)           | Differences a `"timeSeries"` object                       |
| [`scale`](https://geobosh.github.io/timeSeriesDoc/reference/base-scale.md)         | Centers and/or scales a `"timeSeries"` object             |
| [`quantile`](https://geobosh.github.io/timeSeriesDoc/reference/methods-mathOps.md) | Returns quantiles of an univariate `"timeSeries"`         |

## Methods

|                                                                                    |                                                 |
|------------------------------------------------------------------------------------|-------------------------------------------------|
| [`as.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md) | Defines method for a `"timeSeries"`             |
| `as.*.default`                                                                     | Returns the input                               |
| `as.*.ts`                                                                          | Transforma a 'ts' object into a `"timeSeries"`  |
| `as.*.data.frame`                                                                  | Transforms a 'data.frame' intp a 'timeSeries    |
| `as.*.character`                                                                   | Loads and transforms from a demo file           |
| `as.*.zoo`                                                                         | Transforms a 'zoo' object into a `"timeSeries"` |
| `as.vector.*`                                                                      | Converts univariate `"timeSeries"` to vector    |
| `as.matrix.*`                                                                      | Converts `"timeSeries"` to matrix               |
| `as.numeric.*`                                                                     | Converts `"timeSeries"` to numeric              |
| `as.data.frame.*`                                                                  | Converts `"timeSeries"` to data.frame           |
| `as.ts.*`                                                                          | Converts `"timeSeries"` to ts                   |
| `as.logical.*`                                                                     | Converts `"timeSeries"` to logical              |
| [`is.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-is.md) | Tests for a `"timeSeries"` object               |
| [`plot`](https://geobosh.github.io/timeSeriesDoc/reference/methods-plot.md)        | Displays a X-Y `"timeSeries"` Plot              |
| [`lines`](https://geobosh.github.io/timeSeriesDoc/reference/methods-plot.md)       | Adds connected line segments to a plot          |
| [`points`](https://geobosh.github.io/timeSeriesDoc/reference/methods-plot.md)      | Adds Points to a plot                           |
| [`show`](https://geobosh.github.io/timeSeriesDoc/reference/methods-show.md)        | Prints a 'timeSeries oobject                    |

## Financial time series functions

|                                                                                                |                                                     |
|------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| [`align`](https://geobosh.github.io/timeSeriesDoc/reference/fin-align.md)                      | Aligns a `"timeSeries"` to time stamps              |
| [`cumulated`](https://geobosh.github.io/timeSeriesDoc/reference/fin-cumulated.md)              | Computes cumulated series from a returns            |
| [`alignDailySeries`](https://geobosh.github.io/timeSeriesDoc/reference/fin-align.md)           | Aligns a `"timeSeries"` to calendarical dates       |
| [`rollDailySeries`](https://geobosh.github.io/timeSeriesDoc/reference/base-apply.md)           | Rolls a 'timeSeries daily                           |
| [`drawdowns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md)              | Computes series of drawdowns from financial returns |
| [`drawdownsStats`](https://geobosh.github.io/timeSeriesDoc/reference/fin-drawdowns.md)         | Computes drawdowns statistics                       |
| [`durations`](https://geobosh.github.io/timeSeriesDoc/reference/fin-durations.md)              | Computes durations from a financial time series     |
| [`countMonthlyRecords`](https://geobosh.github.io/timeSeriesDoc/reference/fin-monthly.md)      | Counts monthly records in a `"timeSeries"`          |
| [`rollMonthlyWindows`](https://geobosh.github.io/timeSeriesDoc/reference/fin-monthly.md)       | Rolls Monthly windows                               |
| [`rollMonthlySeries`](https://geobosh.github.io/timeSeriesDoc/reference/fin-monthly.md)        | Rolls a `"timeSeries"` monthly                      |
| [`endOfPeriodSeries`](https://geobosh.github.io/timeSeriesDoc/reference/fin-periodical.md)     | Returns end of periodical series                    |
| [`endOfPeriodStats`](https://geobosh.github.io/timeSeriesDoc/reference/fin-periodical.md)      | Returns end of period statistics                    |
| [`endOfPeriodBenchmarks`](https://geobosh.github.io/timeSeriesDoc/reference/fin-periodical.md) | Returns period benchmarks                           |
| [`returns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md)                  | Computes returns from prices or indexes             |
| [`returns0`](https://geobosh.github.io/timeSeriesDoc/reference/fin-returns.md)                 | Computes untrimmed returns from prices or indexes   |
| [`runlengths`](https://geobosh.github.io/timeSeriesDoc/reference/fin-runlengths.md)            | Computes run lenghts of a `"timeSeries"`            |
| [`smoothLowess`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md) | Smoothes a `"timeSeries"`                           |
| [`smoothSpline`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md) | Smoothes a `"timeSeries"`                           |
| [`smoothSupsmu`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md) | Smoothes a `"timeSeries"`                           |
| [`splits`](https://geobosh.github.io/timeSeriesDoc/reference/fin-splits.md)                    | Detects `"timeSeries"` splits by outlier detection  |
| [`spreads`](https://geobosh.github.io/timeSeriesDoc/reference/fin-spreads.md)                  | Computes spreads from a price/index stream          |
| [`turns`](https://geobosh.github.io/timeSeriesDoc/reference/fin-turnpoints.md)                 | Computes turning points in a `"timeSeries"` object  |
| [`turnsStats`](https://geobosh.github.io/timeSeriesDoc/reference/fin-turnpoints.md)            | Computes turning points statistics                  |

## Statistics Time Series functions

|                                                                                                      |                                                           |
|------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| [`colCumsums`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)           | Computes cumulated column sums of a `"timeSeries"`        |
| [`colCummaxs`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)           | Computes cumulated maximum of a `"timeSeries"`            |
| [`colCummins`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)           | Computes cumulated minimum of a `"timeSeries"`            |
| [`colCumprods`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)          | Computes cumulated pruduct values by column               |
| [`colCumreturns`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colCumsums.md)        | Computes cumulated returns by column                      |
| [`colSums`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                 | Computes sums of all values in each column                |
| [`colMeans`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                | Computes means of all values in each column               |
| [`colSds`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                  | Computes standard deviations of all values in each column |
| [`colVars`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                 | Computes variances of all values in each column           |
| [`colSkewness`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)             | Computes skewness of all values in each column            |
| [`colKurtosis`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)             | Computes kurtosis of all values in each column            |
| [`colMaxs`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                 | Computes maxima of all values in each column              |
| [`colMins`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                 | Computes minima of all values in each column              |
| [`colProds`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                | Computes products of all values in each column            |
| [`colStats`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-colSums.md)                | Computes statistics of all values in each column          |
| [`orderColnames`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)     | Returns ordered column names of a `"timeSeries"`          |
| [`sortColnames`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)      | Returns alphabetically sorted column names                |
| [`sampleColnames`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)    | Returns sampled column names of a `"timeSeries"`          |
| [`pcaColnames`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)       | Returns PCA correlation ordered column names              |
| [`hclustColnames`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)    | Returns hierarchically clustered columnames               |
| [`statsColnames`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderColnames.md)     | Returns statisticall rearrange columnames                 |
| [`orderStatistics`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-orderStatistics.md) | Computes order statistics of a `"timeSeries"` object      |
| [`rollMean`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)               | Computes rolling means of a `"timeSeries"` object         |
| [`rollMin`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)                | Computes rolling minima of a `"timeSeries"` object        |
| [`rollMax`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)                | Computes rolling maxima of a `"timeSeries"` object        |
| [`rollMedian`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)             | Computes rolling medians of a `"timeSeries"` object       |
| [`rollStats`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rollMean.md)              | Computes rolling statistics of a `"timeSeries"` objectcr  |
| [`rowCumsums`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-rowCumsums.md)           | Computes cumulated column sums of a `"timeSeries"`        |
| [`smoothLowess`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md)       | Smoothes a series with lowess function                    |
| [`smoothSupsmu`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md)       | Smoothes a series with supsmu function                    |
| [`smoothSpline`](https://geobosh.github.io/timeSeriesDoc/reference/statistics-smoothLowess.md)       | Smoothes a series with smooth.spline function             |

## Misc Functions

|                                                                                            |                                                     |
|--------------------------------------------------------------------------------------------|-----------------------------------------------------|
| [`dummyDailySeries`](https://geobosh.github.io/timeSeriesDoc/reference/fin-dummy.md)       | Creates a dummy daily `"timeSeries"` object         |
| [`isMonthly`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)   | Decides if the series consists of monthly records   |
| [`isDaily`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md)     | Decides if the series consists of daily records     |
| [`isQuarterly`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries-isRegular.md) | Decides if the series consists of Quarterly records |
| [`description`](https://geobosh.github.io/timeSeriesDoc/reference/utils-description.md)    | Creates default description string                  |
