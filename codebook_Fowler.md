Codebook Fowler
================

- [Metadata](#metadata)
  - [Description](#description)
- [Variables](#variables)
  - [Cycle](#Cycle)
    - [Distribution](#Cycle_distribution)
    - [Summary statistics](#Cycle_summary)
  - [FECRecNo](#FECRecNo)
    - [Distribution](#FECRecNo_distribution)
    - [Summary statistics](#FECRecNo_summary)
  - [PACID](#PACID)
    - [Distribution](#PACID_distribution)
    - [Summary statistics](#PACID_summary)
  - [CID](#CID)
    - [Distribution](#CID_distribution)
    - [Summary statistics](#CID_summary)
  - [Candidate_Name_Party](#Candidate_Name_Party)
    - [Distribution](#Candidate_Name_Party_distribution)
    - [Summary statistics](#Candidate_Name_Party_summary)
  - [Senator_ID](#Senator_ID)
    - [Distribution](#Senator_ID_distribution)
    - [Summary statistics](#Senator_ID_summary)
  - [Vote_tax](#Vote_tax)
    - [Distribution](#Vote_tax_distribution)
    - [Summary statistics](#Vote_tax_summary)
  - [vote_care](#vote_care)
    - [Distribution](#vote_care_distribution)
    - [Summary statistics](#vote_care_summary)
  - [Contribution_Amount](#Contribution_Amount)
    - [Distribution](#Contribution_Amount_distribution)
    - [Summary statistics](#Contribution_Amount_summary)
  - [date](#date)
    - [Distribution](#date_distribution)
    - [Summary statistics](#date_summary)
  - [real_code](#real_code)
    - [Distribution](#real_code_distribution)
    - [Summary statistics](#real_code_summary)
  - [PAC_Name](#PAC_Name)
    - [Distribution](#PAC_Name_distribution)
    - [Summary statistics](#PAC_Name_summary)
  - [Type](#Type)
    - [Distribution](#Type_distribution)
    - [Summary statistics](#Type_summary)
  - [DI](#DI)
    - [Distribution](#DI_distribution)
    - [Summary statistics](#DI_summary)
  - [FECCandID F](#FECCandID_F)
    - [Distribution](#FECCandID_F_distribution)
    - [Summary statistics](#FECCandID_F_summary)
- [Missingness report](#missingness-report)
- [Codebook table](#codebook-table)

``` r
library(margins)
library(readxl)
library(varhandle)
library(stargazer)
```

    ## 
    ## Please cite as:

    ##  Hlavac, Marek (2022). stargazer: Well-Formatted Regression and Summary Statistics Tables.

    ##  R package version 5.2.3. https://CRAN.R-project.org/package=stargazer

``` r
library(marginaleffects)
library(lmtest)
```

    ## Loading required package: zoo

    ## 
    ## Attaching package: 'zoo'

    ## The following objects are masked from 'package:base':
    ## 
    ##     as.Date, as.Date.numeric

``` r
library(knitr)
library(broom)
library(car) #for hccm() robust standard errors
```

    ## Loading required package: carData

``` r
library(sandwich)
library(tidyr)
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following object is masked from 'package:car':
    ## 
    ##     recode

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

Here, we’re just setting a few options.

``` r
knitr::opts_chunk$set(
  warning = TRUE, # show warnings during codebook generation
  message = TRUE, # show messages during codebook generation
  error = TRUE, # do not interrupt codebook generation in case of errors,
                # usually better for debugging
  echo = TRUE  # show R code
)
ggplot2::theme_set(ggplot2::theme_bw())
```

Now, we’re preparing our data for the codebook.

``` r
library(codebook)
```

    ## Warning: package 'codebook' was built under R version 4.3.3

``` r
# codebook_data <- codebook::bfi
# to import an SPSS file from the same folder uncomment and edit the line below
# codebook_data <- rio::import("mydata.sav")
# for Stata
# codebook_data <- rio::import("mydata.dta")
# for CSV
# codebook_data <- rio::import("mydata.csv")
codebook_data <- read_excel("D:/10192024_Vote_Bill.xlsx")
# omit the following lines, if your missing values are already properly labelled
codebook_data <- detect_missing(codebook_data,
    only_labelled = TRUE, # only labelled values are autodetected as
                                   # missing
    negative_values_are_missing = FALSE, # negative values are missing values
    ninety_nine_problems = TRUE,   # 99/999 are missing values, if they
                                   # are more than 5 MAD from the median
    )

# If you are not using formr, the codebook package needs to guess which items
# form a scale. The following line finds item aggregates with names like this:
# scale = scale_1 + scale_2R + scale_3R
# identifying these aggregates allows the codebook function to
# automatically compute reliabilities.
# However, it will not reverse items automatically.
codebook_data <- detect_scales(codebook_data)
```

Create codebook

``` r
codebook(codebook_data)
```

### Metadata

#### Description

**Dataset name**: codebook_data

The dataset has N=57067 rows and 15 columns. 56458 rows have no missing
values on any column.

<details>
<summary title="Expand this section to see some additional metadata in a structured format that is useful for search engines">
Metadata for search engines
</summary>

- **Date published**: 2025-01-30

<table class="kable_wrapper">
<tbody>
<tr>
<td>

| x                    |
|:---------------------|
| Cycle                |
| FECRecNo             |
| PACID                |
| CID                  |
| Candidate_Name_Party |
| Senator_ID           |
| Vote_tax             |
| vote_care            |
| Contribution_Amount  |
| date                 |
| real_code            |
| PAC_Name             |
| Type                 |
| DI                   |
| FECCandID F          |

</td>
</tr>
</tbody>
</table>
</details>

## Variables

### Cycle

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_Cycle_distribution-1.png"
alt="Distribution of values for Cycle" />
<figcaption aria-hidden="true">Distribution of values for
Cycle</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name  | data_type | n_missing | complete_rate | min  | median | max  | mean |  sd | hist  | label |
|:------|:----------|----------:|--------------:|:-----|:-------|:-----|-----:|----:|:------|:------|
| Cycle | numeric   |         0 |             1 | 2016 | 2016   | 2016 | 2016 |   0 | ▁▁▇▁▁ | NA    |

### FECRecNo

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_FECRecNo_distribution-16-1.png"
alt="Distribution of values for FECRecNo" />
<figcaption aria-hidden="true">Distribution of values for
FECRecNo</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name     | data_type | n_missing | complete_rate | min   | median  | max     |        mean |           sd | hist  | label |
|:---------|:----------|----------:|--------------:|:------|:--------|:--------|------------:|-------------:|:------|:------|
| FECRecNo | numeric   |         0 |             1 | 1e+18 | 4.1e+18 | 4.1e+18 | 4.02278e+18 | 2.928871e+17 | ▁▁▁▁▇ | NA    |

### PACID

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_PACID_distribution-23-1.png"
alt="Distribution of values for PACID" />
<figcaption aria-hidden="true">Distribution of values for
PACID</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name  | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| PACID | character |         0 |             1 |     2872 |     0 | 9   | 9   |          0 | NA    |

### CID

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_CID_distribution-30-1.png"
alt="Distribution of values for CID" />
<figcaption aria-hidden="true">Distribution of values for
CID</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:-----|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| CID  | character |         0 |             1 |       68 |     0 | 9   | 9   |          0 | NA    |

### Candidate_Name_Party

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_Candidate_Name_Party_distribution-37-1.png"
alt="Distribution of values for Candidate_Name_Party" />
<figcaption aria-hidden="true">Distribution of values for
Candidate_Name_Party</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name                 | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:---------------------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| Candidate_Name_Party | character |         0 |             1 |       68 |     0 | 12  | 26  |          0 | NA    |

### Senator_ID

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_Senator_ID_distribution-44-1.png"
alt="Distribution of values for Senator_ID" />
<figcaption aria-hidden="true">Distribution of values for
Senator_ID</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name       | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:-----------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| Senator_ID | character |         0 |             1 |       68 |     0 | 8   | 22  |          0 | NA    |

### Vote_tax

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_Vote_tax_distribution-51-1.png"
alt="Distribution of values for Vote_tax" />
<figcaption aria-hidden="true">Distribution of values for
Vote_tax</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name     | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:---------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| Vote_tax | character |         0 |             1 |        3 |     0 | 3   | 10  |          0 | NA    |

### vote_care

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_vote_care_distribution-58-1.png"
alt="Distribution of values for vote_care" />
<figcaption aria-hidden="true">Distribution of values for
vote_care</figcaption>
</figure>

4 missing values.

#### Summary statistics

| name      | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:----------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| vote_care | character |         4 |     0.9999299 |        3 |     0 | 3   | 10  |          0 | NA    |

### Contribution_Amount

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_Contribution_Amount_distribution-65-1.png"
alt="Distribution of values for Contribution_Amount" />
<figcaption aria-hidden="true">Distribution of values for
Contribution_Amount</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name                | data_type | n_missing | complete_rate | min     | median | max   |     mean |       sd | hist  | label |
|:--------------------|:----------|----------:|--------------:|:--------|:-------|:------|---------:|---------:|:------|:------|
| Contribution_Amount | numeric   |         0 |             1 | -709224 | 1000   | 3e+06 | 5731.684 | 56617.55 | ▇▁▁▁▁ | NA    |

### date

#### Distribution

    ## 702  unique, categorical values, so not shown.

5 missing values.

#### Summary statistics

| name | data_type | n_missing | complete_rate | n_unique | min        | median     | max        | label |
|:-----|:----------|----------:|--------------:|---------:|:-----------|:-----------|:-----------|:------|
| date | POSIXct   |         5 |     0.9999124 |      702 | 2013-03-21 | 2016-07-11 | 2017-09-07 | NA    |

### real_code

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_real_code_distribution-79-1.png"
alt="Distribution of values for real_code" />
<figcaption aria-hidden="true">Distribution of values for
real_code</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name      | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:----------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| real_code | character |         0 |             1 |      366 |     0 | 5   | 5   |          0 | NA    |

### PAC_Name

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_PAC_Name_distribution-86-1.png"
alt="Distribution of values for PAC_Name" />
<figcaption aria-hidden="true">Distribution of values for
PAC_Name</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name     | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:---------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| PAC_Name | character |         0 |             1 |      369 |     0 | 4   | 50  |          0 | NA    |

### Type

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_Type_distribution-93-1.png"
alt="Distribution of values for Type" />
<figcaption aria-hidden="true">Distribution of values for
Type</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:-----|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| Type | character |         0 |             1 |       10 |     0 | 3   | 3   |          0 | NA    |

### DI

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_DI_distribution-100-1.png"
alt="Distribution of values for DI" />
<figcaption aria-hidden="true">Distribution of values for
DI</figcaption>
</figure>

0 missing values.

#### Summary statistics

| name | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:-----|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| DI   | character |         0 |             1 |        2 |     0 | 1   | 1   |          0 | NA    |

### FECCandID F

#### Distribution

<figure>
<img
src="codebook_Fowler_files/figure-gfm/cb_codebook_data_FECCandID_F_distribution-107-1.png"
alt="Distribution of values for FECCandID F" />
<figcaption aria-hidden="true">Distribution of values for FECCandID
F</figcaption>
</figure>

601 missing values.

#### Summary statistics

| name        | data_type | n_missing | complete_rate | n_unique | empty | min | max | whitespace | label |
|:------------|:----------|----------:|--------------:|---------:|------:|:----|:----|-----------:|:------|
| FECCandID F | character |       601 |     0.9894685 |      110 |     0 | 9   | 9   |          0 | NA    |

## Missingness report

<div data-pagedtable="false">

<script data-pagedtable-source type="application/json">
{"columns":[{"label":["description"],"name":[1],"type":["chr"],"align":["left"]},{"label":["vote_care"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["date"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["FECCandID F"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["var_miss"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["n_miss"],"name":[6],"type":["dbl"],"align":["right"]}],"data":[{"1":"Missing values in 0 variables","2":"1","3":"1","4":"1","5":"0","6":"56458"},{"1":"Missing values per variable","2":"4","3":"5","4":"601","5":"610","6":"610"},{"1":"Missing values in 1 variables","2":"1","3":"1","4":"0","5":"1","6":"600"},{"1":"3 other, less frequent patterns","2":"2","3":"1","4":"2","5":"4","6":"9"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>

</div>

## Codebook table

| name                                                     | data_type | n_missing | complete_rate | n_unique | empty | min        | median     | max        |         mean |           sd | whitespace | hist  | label |
|:---------------------------------------------------------|:----------|----------:|--------------:|---------:|------:|:-----------|:-----------|:-----------|-------------:|-------------:|-----------:|:------|:------|
| <a href="#Cycle">Cycle</a>                               | numeric   |         0 |     1.0000000 |       NA |    NA | 2.0e+03    | 2.0e+03    | 2.0e+03    | 2.016000e+03 | 0.000000e+00 |         NA | ▁▁▇▁▁ | NA    |
| <a href="#FECRecNo">FECRecNo</a>                         | numeric   |         0 |     1.0000000 |       NA |    NA | 1.0e+18    | 4.1e+18    | 4.1e+18    | 4.022780e+18 | 2.928871e+17 |         NA | ▁▁▁▁▇ | NA    |
| <a href="#PACID">PACID</a>                               | character |         0 |     1.0000000 |     2872 |     0 | 9          | NA         | 9          |           NA |           NA |          0 | NA    | NA    |
| <a href="#CID">CID</a>                                   | character |         0 |     1.0000000 |       68 |     0 | 9          | NA         | 9          |           NA |           NA |          0 | NA    | NA    |
| <a href="#Candidate_Name_Party">Candidate_Name_Party</a> | character |         0 |     1.0000000 |       68 |     0 | 12         | NA         | 26         |           NA |           NA |          0 | NA    | NA    |
| <a href="#Senator_ID">Senator_ID</a>                     | character |         0 |     1.0000000 |       68 |     0 | 8          | NA         | 22         |           NA |           NA |          0 | NA    | NA    |
| <a href="#Vote_tax">Vote_tax</a>                         | character |         0 |     1.0000000 |        3 |     0 | 3          | NA         | 10         |           NA |           NA |          0 | NA    | NA    |
| <a href="#vote_care">vote_care</a>                       | character |         4 |     0.9999299 |        3 |     0 | 3          | NA         | 10         |           NA |           NA |          0 | NA    | NA    |
| <a href="#Contribution_Amount">Contribution_Amount</a>   | numeric   |         0 |     1.0000000 |       NA |    NA | -7.1e+05   | 1.0e+03    | 3.0e+06    | 5.731684e+03 | 5.661755e+04 |         NA | ▇▁▁▁▁ | NA    |
| <a href="#date">date</a>                                 | POSIXct   |         5 |     0.9999124 |      702 |    NA | 2013-03-21 | 2016-07-11 | 2017-09-07 |           NA |           NA |         NA | NA    | NA    |
| <a href="#real_code">real_code</a>                       | character |         0 |     1.0000000 |      366 |     0 | 5          | NA         | 5          |           NA |           NA |          0 | NA    | NA    |
| <a href="#PAC_Name">PAC_Name</a>                         | character |         0 |     1.0000000 |      369 |     0 | 4          | NA         | 50         |           NA |           NA |          0 | NA    | NA    |
| <a href="#Type">Type</a>                                 | character |         0 |     1.0000000 |       10 |     0 | 3          | NA         | 3          |           NA |           NA |          0 | NA    | NA    |
| <a href="#DI">DI</a>                                     | character |         0 |     1.0000000 |        2 |     0 | 1          | NA         | 1          |           NA |           NA |          0 | NA    | NA    |
| <a href="#FECCandID_F">FECCandID F</a>                   | character |       601 |     0.9894685 |      110 |     0 | 9          | NA         | 9          |           NA |           NA |          0 | NA    | NA    |

<script type="application/ld+json">
{
  "name": "codebook_data",
  "datePublished": "2025-01-30",
  "description": "The dataset has N=57067 rows and 15 columns.\n56458 rows have no missing values on any column.\n\n\n## Table of variables\nThis table contains variable names, labels, and number of missing values.\nSee the complete codebook for more.\n\n|name                 |label | n_missing|\n|:--------------------|:-----|---------:|\n|Cycle                |NA    |         0|\n|FECRecNo             |NA    |         0|\n|PACID                |NA    |         0|\n|CID                  |NA    |         0|\n|Candidate_Name_Party |NA    |         0|\n|Senator_ID           |NA    |         0|\n|Vote_tax             |NA    |         0|\n|vote_care            |NA    |         4|\n|Contribution_Amount  |NA    |         0|\n|date                 |NA    |         5|\n|real_code            |NA    |         0|\n|PAC_Name             |NA    |         0|\n|Type                 |NA    |         0|\n|DI                   |NA    |         0|\n|FECCandID F          |NA    |       601|\n\n### Note\nThis dataset was automatically described using the [codebook R package](https://rubenarslan.github.io/codebook/) (version 0.9.6).",
  "keywords": ["Cycle", "FECRecNo", "PACID", "CID", "Candidate_Name_Party", "Senator_ID", "Vote_tax", "vote_care", "Contribution_Amount", "date", "real_code", "PAC_Name", "Type", "DI", "FECCandID F"],
  "@context": "https://schema.org/",
  "@type": "Dataset",
  "variableMeasured": [
    {
      "name": "Cycle",
      "@type": "propertyValue"
    },
    {
      "name": "FECRecNo",
      "@type": "propertyValue"
    },
    {
      "name": "PACID",
      "@type": "propertyValue"
    },
    {
      "name": "CID",
      "@type": "propertyValue"
    },
    {
      "name": "Candidate_Name_Party",
      "@type": "propertyValue"
    },
    {
      "name": "Senator_ID",
      "@type": "propertyValue"
    },
    {
      "name": "Vote_tax",
      "@type": "propertyValue"
    },
    {
      "name": "vote_care",
      "@type": "propertyValue"
    },
    {
      "name": "Contribution_Amount",
      "@type": "propertyValue"
    },
    {
      "name": "date",
      "@type": "propertyValue"
    },
    {
      "name": "real_code",
      "@type": "propertyValue"
    },
    {
      "name": "PAC_Name",
      "@type": "propertyValue"
    },
    {
      "name": "Type",
      "@type": "propertyValue"
    },
    {
      "name": "DI",
      "@type": "propertyValue"
    },
    {
      "name": "FECCandID F",
      "@type": "propertyValue"
    }
  ]
}
</script>
<details>
<summary>
JSON-LD metadata
</summary>

The following JSON-LD can be found by search engines, if you share this
codebook publicly on the web.

``` json
{
  "name": "codebook_data",
  "datePublished": "2025-01-30",
  "description": "The dataset has N=57067 rows and 15 columns.\n56458 rows have no missing values on any column.\n\n\n## Table of variables\nThis table contains variable names, labels, and number of missing values.\nSee the complete codebook for more.\n\n|name                 |label | n_missing|\n|:--------------------|:-----|---------:|\n|Cycle                |NA    |         0|\n|FECRecNo             |NA    |         0|\n|PACID                |NA    |         0|\n|CID                  |NA    |         0|\n|Candidate_Name_Party |NA    |         0|\n|Senator_ID           |NA    |         0|\n|Vote_tax             |NA    |         0|\n|vote_care            |NA    |         4|\n|Contribution_Amount  |NA    |         0|\n|date                 |NA    |         5|\n|real_code            |NA    |         0|\n|PAC_Name             |NA    |         0|\n|Type                 |NA    |         0|\n|DI                   |NA    |         0|\n|FECCandID F          |NA    |       601|\n\n### Note\nThis dataset was automatically described using the [codebook R package](https://rubenarslan.github.io/codebook/) (version 0.9.6).",
  "keywords": ["Cycle", "FECRecNo", "PACID", "CID", "Candidate_Name_Party", "Senator_ID", "Vote_tax", "vote_care", "Contribution_Amount", "date", "real_code", "PAC_Name", "Type", "DI", "FECCandID F"],
  "@context": "https://schema.org/",
  "@type": "Dataset",
  "variableMeasured": [
    {
      "name": "Cycle",
      "@type": "propertyValue"
    },
    {
      "name": "FECRecNo",
      "@type": "propertyValue"
    },
    {
      "name": "PACID",
      "@type": "propertyValue"
    },
    {
      "name": "CID",
      "@type": "propertyValue"
    },
    {
      "name": "Candidate_Name_Party",
      "@type": "propertyValue"
    },
    {
      "name": "Senator_ID",
      "@type": "propertyValue"
    },
    {
      "name": "Vote_tax",
      "@type": "propertyValue"
    },
    {
      "name": "vote_care",
      "@type": "propertyValue"
    },
    {
      "name": "Contribution_Amount",
      "@type": "propertyValue"
    },
    {
      "name": "date",
      "@type": "propertyValue"
    },
    {
      "name": "real_code",
      "@type": "propertyValue"
    },
    {
      "name": "PAC_Name",
      "@type": "propertyValue"
    },
    {
      "name": "Type",
      "@type": "propertyValue"
    },
    {
      "name": "DI",
      "@type": "propertyValue"
    },
    {
      "name": "FECCandID F",
      "@type": "propertyValue"
    }
  ]
}`
```

</details>
