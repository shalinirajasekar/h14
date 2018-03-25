Section I. High-Applicant Employers:

1.  Which Employers send most number of H-1B visa applications?

2.  What is the Percentage share out of the 85,000 visa cap for the Employers with most applications?

Let's begin the analysis by loading the libraries and the dataframe!

``` r
library(dplyr)
```

    ##
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ##
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ##
    ##     intersect, setdiff, setequal, union

``` r
library(ggplot2)
library(ggrepel)
library(ggmap)
```

    ## Google Maps API Terms of Service: http://developers.google.com/maps/terms.

    ## Please cite ggmap if you use it: see citation("ggmap") for details.

``` r
source("helpers.R")
```

    ## Loading required package: lazyeval

helpers.R includes a suite of plotting and filter functions that will help us with the data analysis.

``` r
h1b_df <- readRDS("h1b_transformed.rds")

colnames(h1b_df)
```

    ##  [1] "CASE_NUMBER"         "CASE_STATUS"         "EMPLOYER_NAME"      
    ##  [4] "SOC_NAME"            "SOC_CODE"            "JOB_TITLE"          
    ##  [7] "FULL_TIME_POSITION"  "PREVAILING_WAGE"     "WORKSITE_CITY"      
    ## [10] "WORKSITE_STATE_ABB"  "YEAR"                "WORKSITE_STATE_FULL"
    ## [13] "WORKSITE"            "lon"                 "lat"                
    ## [16] "COLI"

<h2>
High-Applicant Employers
</h2>
In this sub-section, I analyze employers with high number of applications. Let's begin by finding out the top 10 employers with the most number of applications in the period 2011-2016.

It might occur that Employer Names takes most of the space leaving almost little for the actual plot. For this purpose, I cut short Employer names to only the first word in their title. An another approach might be reducing the axis.text size for ggplot2.

``` r
h1b_df$EMPLOYER_COMPACT = sapply(h1b_df$EMPLOYER_NAME,split_first,split = " ")
```

``` r
input <- plot_input(h1b_df, "EMPLOYER_NAME", "YEAR", "TotalApps",filter = TRUE, Ntop = 10)

g <- plot_output(input, 'EMPLOYER_NAME','YEAR','TotalApps', 'EMPLOYER','TOTAL NO. of APPLICATIONS') + theme(axis.title = element_text(size = rel(1.5)),
          axis.text.y = element_text(size=rel(0.85),face="bold"))
g
```

![](data_analysis_files/figure-markdown_github/unnamed-chunk-4-1.png)

Observations:

1.  Infosys leads the pack by a huge margin with over 30000 applications in 2013 and 2015.

2.  The Top 10 list is dominated by the Indian IT companies.

3.  We observe a slight dip in the number of applications from Infosys, Wipro, Tata Consultancy, IBM India and HCL America. This is because of increased incorporation of automation in the IT industry. 
