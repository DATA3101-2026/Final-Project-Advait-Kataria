# AI Data Center Power Use vs. Industry Growth: Data Audit
Advait Kataria
2026-11-05

- [1: Project Overview](#1-project-overview)
- [2: Data Sources](#2-data-sources)
  - [2.1 Summary of sources](#21-summary-of-sources)
  - [2.2.1: Epoch AI Frontier Data
    Centers](#221-epoch-ai-frontier-data-centers)
  - [2.2.2 Statistics Canada Table 36-10-0434-01, GDP by
    industry](#222-statistics-canada-table-36-10-0434-01-gdp-by-industry)
  - [2.2.3: Statistics Canada Table 33-10-1167-01, AI use by
    industry](#223-statistics-canada-table-33-10-1167-01-ai-use-by-industry)
  - [2.3: Investigated and rejected
    sources](#23-investigated-and-rejected-sources)
  - [2.4: What I could not find](#24-what-i-could-not-find)
- [3: Licensing and permissions](#3-licensing-and-permissions)
  - [3.1: Licence by source](#31-licence-by-source)
  - [3.3: Downstream permissions](#33-downstream-permissions)
- [4: Consent and identifiability](#4-consent-and-identifiability)
- [5: Exclusions and harms](#5-exclusions-and-harms)
  - [5.1: Excluded data from the
    audit](#51-excluded-data-from-the-audit)
  - [5.2: Who could be harmed](#52-who-could-be-harmed)
  - [5.3: Unreleased working data](#53-unreleased-working-data)
- [6: Data Stewardship](#6-data-stewardship)
- [7: Use of AI](#7-use-of-ai)
- [8: Session information](#8-session-information)

# 1: Project Overview

The goal of this project is to see how the rapid growth in AI data
center power capacity coincide with growth in Canada’s high-AI
industries than its low-AI industries. The project through various data
sources will visualize the variables contributing to this comparison.

------------------------------------------------------------------------

# 2: Data Sources

<!-- For the section numbers above, remember to update if needed for multiple sources or removing unneeded subsections -->

\[This section covers everything you went looking for in your data
audit. If you found sources that you chose not to use for the project
itself, put them in! That helps your reader understand all the options
you were considering as you worked through it.\]

## 2.1 Summary of sources

\[Fill in one row per source you investigated. Include the ones you
rejected in the `Using?` column. This table is the quick reference your
reader checks before reading anything else. A clear table will give a
reader a good idea of what the focus is beyond the overview.\]

| Source | Producer | Format | Coverage | Using |
|:---|:---|:---|:---|:---|
| Epoch AI Frontier Data Centers | Epoch AI | CSV (7 files) | 96 AI data centres, 12 countries, 2018-2030 (incl. projections) | Yes |
| StatCan Table 36-10-0434-01, GDP by industry | Statistics Canada | CSV | Canada, monthly, by NAICS industry | Yes |
| StatCan Table 33-10-1167-01, AI use by industry | Statistics Canada | CSV | Canada and provinces, Q2 2026, by NAICS industry | Yes |
| Epoch AI Models | Epoch AI | CSV | Global, AI models since 1950s | No, see 2.3 |
| LBNL 2024 US Data Center Energy Usage Report | Lawrence Berkeley National Laboratory | PDF | United States, 2014-2028 | No, see 2.3 |
| SEC EDGAR Financial Statement Data Sets | US Securities and Exchange Commission | TSV (quarterly ZIPs) | US public companies, 2009 onward | No, see 2.3 |
| OpenAlex | OurResearch (nonprofit) | API | Global research papers | No, see 2.3 |
| StatCan Table 33-10-1045-01, planned AI use | Statistics Canada | CSV | Canada, Q3 2025 | No, see 2.3 |

## 2.2.1: Epoch AI Frontier Data Centers

**Producer and authority.** Epoch AI, an independent research institute
founded in 2021 that studies the trajectory of AI. No government
mandate. It is a data-first research nonprofit investigating artificial
intelligence.

**Original Dataset Purpose.** Built to track construction timelines of
major AI data centers: power capacity, compute capacity and capital cost
over time. Not built to measure electricity actually consumed.

**Collection method.** Estimated from high-resolution satellite imagery,
permits and public documents. The download includes reference tables of
chillers (143 models) and cooling towers (527 models), which Epoch uses
to estimate a site’s power from the cooling equipment visible in
satellite images. Epoch states 80% confidence that a given power
capacity is accurate.

**Coverage and resolution.** 96 data centers in 12 countries. Timeline
file: 575 dated records, December 2018 to January 2030. Unit of
observation: one site (data_centers.csv) or one site on one date
(data_center_timelines.csv).

**Licence.** Creative Commons Attribution 4.0 (CC BY 4.0).

**Access.** Downloaded as a ZIP of seven CSV files plus a README from
the Epoch AI data centers downloads page
(https://epoch.ai/data/data-centers-documentation/downloads). Can be
downloaded from Epoch AI’s website for future use though it may differ
from the file used here.

**Known problems.** A few problems are:- -20 sites show 0 MW current
power (likely planned or under construction). -Only 28 timeline records
come from before 2023. -Capacity is not consumption (Epoch: typically
60-80% of capacity).

    Rows: 96
    Columns: 16
    $ Name                                             <chr> "Colossus 2", "OpenAI…
    $ `Current H100 equivalents`                       <dbl> 1111672.6, 1018696.3,…
    $ `Current power (MW)`                             <dbl> 946.0000, 824.0000, 1…
    $ `Current total capital cost (2025 USD billions)` <dbl> 35.836372, 31.214768,…
    $ Owner                                            <chr> "SpaceXAI #confident"…
    $ Users                                            <chr> "Anthropic #confident…
    $ `Selected Sources`                               <chr> "- [WSJ profile of th…
    $ `Calculations sheet`                             <chr> "https://docs.google.…
    $ Project                                          <chr> NA, "Stargate #confid…
    $ `Current chip types`                             <chr> "B200,B300", "B200,B3…
    $ `All chip types`                                 <chr> "B200,B300", "B200,B3…
    $ Investors                                        <chr> NA, "Softbank,OpenAI,…
    $ `Construction companies`                         <chr> NA, "Mortenson", NA, …
    $ `Energy companies`                               <chr> NA, "American Electri…
    $ Country                                          <chr> "United States", "Uni…
    $ Address                                          <chr> "5420 Tulane Rd, Memp…

    Rows: 575
    Columns: 14
    $ `Data center`                                 <chr> "Colossus 2", "Colossus …
    $ Date                                          <date> 2025-02-28, 2025-09-08,…
    $ `Construction status`                         <chr> "Land clearing begins ne…
    $ `Buildings operational`                       <dbl> 0, 0, 1, 1, 1, 2, 3, 0, …
    $ `IT power (MW)`                               <dbl> 0, 0, 239, 239, 490, 946…
    $ `Power (MW)`                                  <dbl> 0, 0, 323, 323, 661, 127…
    $ `H100 equivalents`                            <dbl> 0.0, 0.0, 277918.1, 2779…
    $ `Performance (8-bit OP/s)`                    <dbl> 0.00000e+00, 0.00000e+00…
    $ `Total capital cost (2025 USD billions)`      <dbl> 0.000000, 0.000000, 9.05…
    $ `Compute cost (2025 USD billions)`            <dbl> 0.000000, 0.000000, 6.24…
    $ `Construction cost (2025 USD billions)`       <dbl> 0.000000, 0.000000, 2.81…
    $ `Annual operating cost (2025 USD billions)`   <dbl> 0.000000, 0.000000, 0.21…
    $ `Water use (MGD)`                             <dbl> NA, NA, NA, NA, NA, NA, …
    $ `Current H100 equivalents (from Data center)` <dbl> 1111672.6, 1111672.6, 11…

## 2.2.2 Statistics Canada Table 36-10-0434-01, GDP by industry

**Producer and authority.** Statistics Canada is Canada’s national
statistical agency, which collects and publishes data under the
Statistics Act. Statistics Canada is committed to transparency and
accountability by providing access to its information in response to
access to information or privacy requests where permitted by law.

**Original Dataset Purpose.** Part of Canada’s national accounts;
measures monthly economic output (GDP at basic prices) of each industry,
used to track the economy.

**Collection method.** Data are extracted from administrative files and
derived from other Statistics Canada surveys and other sources.

**Coverage and resolution.** Canada only

**Licence.** Statistics Canada Open Licence.

**Access.** Downloaded as a full-table CSV (data file plus metadata
file) from
https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=3610043401. Can be
downloaded for future use to study the year used.

**Known problems.** long format with several rows per month per industry
(seasonal adjustment and price types). Industry list is broader than the
AI survey’s sectors

    Rows: 265,932
    Columns: 17
    $ REF_DATE                                                <chr> "1997-01", "19…
    $ GEO                                                     <chr> "Canada", "Can…
    $ DGUID                                                   <chr> "2021A00001112…
    $ `Seasonal adjustment`                                   <chr> "Seasonally ad…
    $ Prices                                                  <chr> "Chained (2017…
    $ `North American Industry Classification System (NAICS)` <chr> "All industrie…
    $ UOM                                                     <chr> "Dollars", "Do…
    $ UOM_ID                                                  <dbl> 81, 81, 81, 81…
    $ SCALAR_FACTOR                                           <chr> "millions", "m…
    $ SCALAR_ID                                               <dbl> 6, 6, 6, 6, 6,…
    $ VECTOR                                                  <chr> "v65201210", "…
    $ COORDINATE                                              <chr> "1.1.1.1", "1.…
    $ VALUE                                                   <dbl> 1200427, 38253…
    $ STATUS                                                  <chr> NA, NA, NA, ".…
    $ SYMBOL                                                  <lgl> NA, NA, NA, NA…
    $ TERMINATED                                              <lgl> NA, NA, NA, NA…
    $ DECIMALS                                                <dbl> 0, 0, 0, 0, 0,…

## 2.2.3: Statistics Canada Table 33-10-1167-01, AI use by industry

**Producer and authority.** Statistics Canada, under the Statistics Act,
through the Canadian Survey on Business Conditions.

**Original Dataset Purpose.** The survey tracks the environment
businesses operate in and their expectations

**Collection method.** Collected through online questionnaire.
Self-reported: businesses may define “using AI” differently

**Coverage and resolution.** Covers Canada. 20 AI-use categories (Yes,
No, 18 application types). Values are percent of businesses.

**Licence.** Statistics Canada Open Licence.

**Access.** Downloaded as a full-table CSV (data file plus metadata
file) from
https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=3310116701.

**Known problems.** Survey excludes some industries in the GDP table and
lots of missing values.

    Rows: 18,760
    Columns: 16
    $ REF_DATE                                                                                                                               <dbl> …
    $ GEO                                                                                                                                    <chr> …
    $ DGUID                                                                                                                                  <chr> …
    $ `Business characteristics`                                                                                                             <chr> …
    $ `Use of artificial intelligence (AI) by businesses or organizations in producing goods or delivering services over the last 12 months` <chr> …
    $ UOM                                                                                                                                    <chr> …
    $ UOM_ID                                                                                                                                 <dbl> …
    $ SCALAR_FACTOR                                                                                                                          <chr> …
    $ SCALAR_ID                                                                                                                              <dbl> …
    $ VECTOR                                                                                                                                 <chr> …
    $ COORDINATE                                                                                                                             <chr> …
    $ VALUE                                                                                                                                  <dbl> …
    $ STATUS                                                                                                                                 <chr> …
    $ SYMBOL                                                                                                                                 <lgl> …
    $ TERMINATED                                                                                                                             <lgl> …
    $ DECIMALS                                                                                                                               <dbl> …

## 2.3: Investigated and rejected sources

- Epoch AI Models: Training energy available for few models, falling to
  30 in 2025 and 3 in 2026 because companies stopped disclosing and
  covers training only, not running models.

-LBNL 2024 report: Published as PDF tables, covers all data centers(not
only AI), and no licence statement found.

-SEC EDGAR: company revenue for all US public companies, but quarterly
files are large.

-StatCan Table 33-10-1045-01: measures planned AI use over the next 12
months, not actual use.

## 2.4: What I could not find

Could not find a Canadian or government dataset of AI data center
electricity use. Later found out that companies such as Google,
Microsoft and xAI do not publish per-site electricity consumption.
Statistics Can also has no data center electricity table.

------------------------------------------------------------------------

# 3: Licensing and permissions

## 3.1: Licence by source

| Source | Licence | Attribution_required | Attribution_given |
|:---|:---|:---|:---|
| Epoch AI Frontier Data Centers | CC BY 4.0 | Yes | Yes, see below |
| StatCan Table 36-10-0434-01, GDP by industry | Statistics Canada Open Licence | Yes | Yes, see below |
| StatCan Table 33-10-1167-01, AI use by industry | Statistics Canada Open Licence | Yes | Yes, see below |

**Attribution statements.** Epoch AI: Epoch AI, ‘AI data centers’.
Published online at epoch.ai. Retrieved from
‘https://epoch.ai/data/ai-data-centers’ \[online resource\].

Statistics Canada table: \> Statistics Canada. Table 36-10-0434-01 Gross
domestic product (GDP) at basic prices, by industry, monthly. DOI:
https://doi.org/10.25318/3610043401-eng

Statistics Canada table: Statistics Canada. Table 33-10-1167-01 Use of
artificial intelligence by businesses and organizations in producing
goods or delivering services over the last 12 months, second quarter of
2026. DOI: https://doi.org/10.25318/3310116701-eng

## 3.3: Downstream permissions

All of the data used in this project is open data. The code in this
repository is covered by the MIT licence included in the repo, so anyone
can reuse or modify it. Both licences(CC BY 4.0 and Statistics Canada
Open Licence) allow the data to be used, modified and shared, as long as
the original source is credited. Anyone reusing this project’s data must
credit Epoch AI and Statistics Canada as the original sources, as well
as this project.

------------------------------------------------------------------------

# 4: Consent and identifiability

None of the data used in this project describes individual people.
EpochAI describes facilities and the companies that own them, StatCan
GDP is industry totals and the AI table reports weighted percentages of
businesses. However the raw AI table also contains rows by majority
ownership group(First Nations, Métis or Inuit).

**Consent.** Built from from satellite imagery, companies that own them
permits EpochAI so no individuals were asked to provide information. The
two Statistics Canada tables come from surveys of businesses, collected
under the Statistics Act.

**Identifiability.** None of the data I analyze describes individual
people. Some of the provincial groups used in GDP data are very small
which is why Statistics Canada has marked many of those cells as too
unreliable to publish or left them blank.

**How sensitive data will be used.** I will keep the raw AI-use file
unchanged, exactly as Statistics Canada published it, but my code will
filter it to national industry rows only. My cleaned dataset and results
will not include any breakdowns by province or by ownership group.

------------------------------------------------------------------------

# 5: Exclusions and harms

## 5.1: Excluded data from the audit

Data that will not be used: Columns dropped from Epoch data (Investors,
Construction companies, Energy companies, Project, mostly blank) as they
describe who funded or built each site, which has nothing to do with the
question about power use. Statistic Can AI rows by ownership group will
not be used as question compares industries, not types of business
owners. The four Epoch files not used (chip types, chip quantities,
chillers, cooling towers) as they describe computing hardware (which
chips and how many) not resource use. As our cost side is power, which
the timelines file already gives.

## 5.2: Who could be harmed

Communities near the data centers as the data is collected from
satellite images.

## 5.3: Unreleased working data

I do not have any working data that I would keep unpublished.

------------------------------------------------------------------------

# 6: Data Stewardship

**Where it lives.**The project lives in a public GitHub repository in
the DATA3101-2026 organization. Because it is public, I plan to move it
to my personal GitHub account.

**Who maintains it.** I maintain it during and after the course.

**Formats and dependencies.** The raw and cleaned data are CSV files.
The code depends on R and the tidyverse packages

**Lifespan.** The data is a snapshot from November 2026. The project
should remain useful as a record of 2022 to 2026, but anyone studying
later years would need to download newer data.

------------------------------------------------------------------------

# 7: Use of AI

AI will only be used in this project to clean and tidy code.

------------------------------------------------------------------------

# 8: Session information

    R version 4.6.1 (2026-06-24)
    Platform: aarch64-apple-darwin23
    Running under: macOS Golden Gate 27.0.1

    Matrix products: default
    BLAS:   /Library/Frameworks/R.framework/Versions/4.6/Resources/lib/libRblas.0.dylib 
    LAPACK: /Library/Frameworks/R.framework/Versions/4.6/Resources/lib/libRlapack.dylib;  LAPACK version 3.12.1

    locale:
    [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

    time zone: America/Moncton
    tzcode source: internal

    attached base packages:
    [1] stats     graphics  grDevices utils     datasets  methods   base     

    other attached packages:
     [1] lubridate_1.9.5 forcats_1.0.1   stringr_1.6.0   dplyr_1.2.1    
     [5] purrr_1.2.2     readr_2.2.0     tidyr_1.3.2     tibble_3.3.1   
     [9] ggplot2_4.0.3   tidyverse_2.0.0

    loaded via a namespace (and not attached):
     [1] bit_4.6.0          gtable_0.3.6       jsonlite_2.0.0     crayon_1.5.3      
     [5] compiler_4.6.1     tidyselect_1.2.1   parallel_4.6.1     scales_1.4.0      
     [9] yaml_2.3.12        fastmap_1.2.0      R6_2.6.1           generics_0.1.4    
    [13] knitr_1.52         pillar_1.11.1      RColorBrewer_1.1-3 tzdb_0.5.0        
    [17] rlang_1.3.0        stringi_1.8.9      xfun_0.60          S7_0.2.2          
    [21] bit64_4.8.6        otel_0.2.0         timechange_0.4.0   cli_3.6.6         
    [25] withr_3.0.3        magrittr_2.0.5     digest_0.6.39      grid_4.6.1        
    [29] vroom_1.7.1        rstudioapi_0.19.0  hms_1.1.4          lifecycle_1.0.5   
    [33] vctrs_0.7.3        evaluate_1.0.5     glue_1.8.1         farver_2.1.2      
    [37] rmarkdown_2.32     tools_4.6.1        pkgconfig_2.0.3    htmltools_0.5.9   
