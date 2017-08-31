mschart R package
================

<!-- README.md is generated from README.Rmd. Please edit that file -->
[![Build Status](https://travis-ci.org/ardata-fr/mschart.svg?branch=master)](https://travis-ci.org/ardata-fr/mschart)

The `mschart` package provides a framework for easily create charts for 'Microsoft PowerPoint' documents. It has to be used with package `officer` that will produce the charts in new or existing PowerPoint or Word documents.

<img src="tools/ms_barchart.png" align="center"/>

Installation
------------

You can install the package from github with:

``` r
# install.packages("devtools")
devtools::install_github("ardata-fr/mschart")
```

Example
-------

This is a basic example which shows you how to create a line chart.

``` r
library(mschart)
library(officer)

linec <- ms_linechart(data = iris, x = "Sepal.Length",
                      y = "Sepal.Width", group = "Species")
linec <- chart_ax_y(linec, num_fmt = "0.00", rotation = -90)
```

Then use package `officer` to send the object as a chart.

``` r
doc <- read_pptx()
doc <- add_slide(doc, layout = "Title and Content", master = "Office Theme")
doc <- ph_with_chart(doc, chart = linec)

print(doc, target = "example.pptx")
```
