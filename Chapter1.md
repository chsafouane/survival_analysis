Chapter1
================
Safouane Chergui

The packages loaded below are needed to execute the code in this file.

``` r
library(asaur)
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.6.1

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

## 1st exercise

The dataset listing the patient, the survival time as well as the
censoring indicator.

``` r
patient_data <- data.frame(
  "Patient" = 1:5,
  "SurvTime" = c(5, 5, 4, 3, 1),
  "Status" = c(0, 0, 1, 1, 1)
)

patient_data
```

    ##   Patient SurvTime Status
    ## 1       1        5      0
    ## 2       2        5      0
    ## 3       3        4      1
    ## 4       4        3      1
    ## 5       5        1      1

``` r
dead <- sum(patient_data$Status)
```

The number of deceased persons during the trial is 3.

Person-years in the trial: is a summary statistic that can be calculated
by summing the total survival time of all patients in the trial
(<https://www.eupati.eu/glossary/patient-years/>)

``` r
person_years <- sum(patient_data$SurvTime)
```

Person-years is equal to 18.

The death rate per person-year: As the name of the statistic suggests,
one has to divide the number of dead persons during the trial by the
previously calculated statistic person\_years.

``` r
death_rate <- dead / person_years
```

The death rate is 0.1666667.

## 2nd exercise

``` r
n_event <- gastricXelox %>% 
  select(delta) %>% 
  sum(.)
```

The number of persons that had the event is 32.

The gastricXelox dataset contains only phase 2 clinical trial.

``` r
person_weeks <- sum(gastricXelox$timeWeeks)
```

The number of person-weeks is 2866.

The event rate per person-week is a similar idea to death-rate that
we’ve calculated in the 1st exercise.

``` r
event_rate <- n_event / person_weeks
```

The event rate per person-week is 0.0111654.
