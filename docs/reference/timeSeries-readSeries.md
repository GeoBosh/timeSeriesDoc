# Read a 'timeSeries' from a text file

Reads a file in table format and creates a `"timeSeries"` object from
it. The first column of the table must hold the timestamps.

## Usage

``` r
readSeries(file, header = TRUE, sep = ";", zone = "", 
    FinCenter = "", format, ...)
```

## Arguments

- file:

  the filename of a spreadsheet dataset from which to import the data
  records.

- header:

  a logical value indicating whether the file contains the names of the
  variables as its first line. If missing, the value is determined from
  the file format: 'header' is set to 'TRUE' if and only if the first
  row contains one fewer fields than the number of columns.

- sep:

  the field seperator used in the spreadsheet file to separate columns,
  by default `";"`. If `sep = ";"` and reading the series fails, then
  the reading is automatically repeated with `sep=","`.

- zone:

  the time zone or financial center where the data were recorded. By
  default `zone = ""` which is short for GMT.

- FinCenter:

  a character with the the location of the financial center named as
  "continent/city".

- format:

  a character string with the format in POSIX notation specifying the
  timestamp format. The format has not to be specified if the first
  column in the file has the timestamp format specifier, e.g. "%Y-%m-%d"
  for the short ISO 8601 format.

- ...:

  Additional arguments passed to
  [`read.table()`](https://rdrr.io/r/utils/read.table.html) which is
  used to read the file.

## Details

The file is imported with
[`read.table`](https://rdrr.io/r/utils/read.table.html). Note the
different default for argument `"sep"`.

The first column of the table must hold the timestamps. Format of the
timestamps can be either specified in the header of the first column or
by the `format` argument.

## Value

an object of class `"timeSeries"`

## See also

[`as.timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/methods-as.md),
[`timeSeries`](https://geobosh.github.io/timeSeriesDoc/reference/timeSeries.md),
[`dummyMonthlySeries`](https://geobosh.github.io/timeSeriesDoc/reference/fin-dummy.md),
[`dummyDailySeries`](https://geobosh.github.io/timeSeriesDoc/reference/fin-dummy.md)

## Examples

``` r
## full path to an example file
fn <- system.file("extdata/msft.csv", package = "timeSeries")
## first few lines of the file
readLines(fn, n = 5)
#> [1] "\"%Y-%m-%d\";Open;High;Low;Close;Volume"           
#> [2] "2000-09-27;63.4375;63.5625;59.8125;60.625;53077800"
#> [3] "2000-09-28;60.8125;61.875;60.625;61.3125;26180200" 
#> [4] "2000-09-29;61;61.3125;58.625;60.3125;37026800"     
#> [5] "2000-10-02;60.5;60.8125;58.25;59.125;29281200"     

## import the file
msft <- readSeries(fn)
head(msft)
#> GMT 
#>               Open    High     Low   Close   Volume
#> 2000-09-27 63.4375 63.5625 59.8125 60.6250 53077800
#> 2000-09-28 60.8125 61.8750 60.6250 61.3125 26180200
#> 2000-09-29 61.0000 61.3125 58.6250 60.3125 37026800
#> 2000-10-02 60.5000 60.8125 58.2500 59.1250 29281200
#> 2000-10-03 59.5625 59.8125 56.5000 56.5625 42687000
#> 2000-10-04 56.3750 56.5625 54.5000 55.4375 68226700

## is msft the same as the data object MSFT?
all.equal(msft, MSFT) 
#> [1] "Attributes: < Component “documentation”: 1 string mismatch >"
## ... almost, except for slot 'documentation'
c(msft@documentation, MSFT@documentation)
#> [1] "Fri Dec 12 16:49:44 2025" ""                        
## actually, all.equal() says 'attribute', not slot. this is ok too:
c(attr(MSFT, "documentation"), attr(msft, "documentation"))
#> [1] ""                         "Fri Dec 12 16:49:44 2025"
## make 'documentation' equal, here "", and compare again:
msft@documentation <- ""
all.equal(msft, MSFT) # TRUE
#> [1] TRUE
```
