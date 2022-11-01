Data import
================

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.5 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.0      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.2      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

## Data Import: CSVs

Let’s import data using the ‘reader’ package

``` r
litters_df = read_csv("data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor :: clean_names(litters_df)
```

Look at the data

``` r
litters_df
```

    ## # A tibble: 49 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_…¹ pups_…² pups_…³ pups_…⁴
    ##    <chr> <chr>                <dbl>       <dbl>    <dbl>   <dbl>   <dbl>   <dbl>
    ##  1 Con7  #85                   19.7        34.7       20       3       4       3
    ##  2 Con7  #1/2/95/2             27          42         19       8       0       7
    ##  3 Con7  #5/5/3/83/3-3         26          41.4       19       6       0       5
    ##  4 Con7  #5/4/2/95/2           28.5        44.1       19       5       1       4
    ##  5 Con7  #4/2/95/3-3           NA          NA         20       6       0       6
    ##  6 Con7  #2/2/95/3-2           NA          NA         20       6       0       4
    ##  7 Con7  #1/5/3/83/3-3/2       NA          NA         20       9       0       9
    ##  8 Con8  #3/83/3-3             NA          NA         20       9       1       8
    ##  9 Con8  #2/95/3               NA          NA         20       8       0       8
    ## 10 Con8  #3/5/2/2/95           28.5        NA         20       8       0       8
    ## # … with 39 more rows, and abbreviated variable names ¹​gd_of_birth,
    ## #   ²​pups_born_alive, ³​pups_dead_birth, ⁴​pups_survive

head(litters_df) tail(litters_df)

``` r
view(lutters_df)
```

``` r
skimr::skim(litters_df)
```

|                                                  |            |
|:-------------------------------------------------|:-----------|
| Name                                             | litters_df |
| Number of rows                                   | 49         |
| Number of columns                                | 8          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |            |
| Column type frequency:                           |            |
| character                                        | 2          |
| numeric                                          | 6          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |            |
| Group variables                                  | None       |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| group         |         0 |             1 |   4 |   4 |     0 |        6 |          0 |
| litter_number |         0 |             1 |   3 |  15 |     0 |       49 |          0 |

**Variable type: numeric**

| skim_variable   | n_missing | complete_rate |  mean |   sd |   p0 |   p25 |   p50 |   p75 | p100 | hist  |
|:----------------|----------:|--------------:|------:|-----:|-----:|------:|------:|------:|-----:|:------|
| gd0_weight      |        15 |          0.69 | 24.38 | 3.28 | 17.0 | 22.30 | 24.10 | 26.67 | 33.4 | ▃▇▇▆▁ |
| gd18_weight     |        17 |          0.65 | 41.52 | 4.05 | 33.4 | 38.88 | 42.25 | 43.80 | 52.7 | ▃▃▇▂▁ |
| gd_of_birth     |         0 |          1.00 | 19.65 | 0.48 | 19.0 | 19.00 | 20.00 | 20.00 | 20.0 | ▅▁▁▁▇ |
| pups_born_alive |         0 |          1.00 |  7.35 | 1.76 |  3.0 |  6.00 |  8.00 |  8.00 | 11.0 | ▁▃▂▇▁ |
| pups_dead_birth |         0 |          1.00 |  0.33 | 0.75 |  0.0 |  0.00 |  0.00 |  0.00 |  4.0 | ▇▂▁▁▁ |
| pups_survive    |         0 |          1.00 |  6.41 | 2.05 |  1.0 |  5.00 |  7.00 |  8.00 |  9.0 | ▁▃▂▇▇ |

“read_csv” options

``` r
read.csv("data/FAS_litters.csv", na = c("", "NA"), skip = 2)
```

    ##    Con7      X.1.2.95.2  X27  X42 X19 X8 X0 X7
    ## 1  Con7   #5/5/3/83/3-3 26.0 41.4  19  6  0  5
    ## 2  Con7     #5/4/2/95/2 28.5 44.1  19  5  1  4
    ## 3  Con7     #4/2/95/3-3   NA   NA  20  6  0  6
    ## 4  Con7     #2/2/95/3-2   NA   NA  20  6  0  4
    ## 5  Con7 #1/5/3/83/3-3/2   NA   NA  20  9  0  9
    ## 6  Con8       #3/83/3-3   NA   NA  20  9  1  8
    ## 7  Con8         #2/95/3   NA   NA  20  8  0  8
    ## 8  Con8     #3/5/2/2/95 28.5   NA  20  8  0  8
    ## 9  Con8     #5/4/3/83/3 28.0   NA  19  9  0  8
    ## 10 Con8   #1/6/2/2/95-2   NA   NA  20  7  0  6
    ## 11 Con8 #3/5/3/83/3-3-2   NA   NA  20  8  0  8
    ## 12 Con8       #2/2/95/2   NA   NA  19  5  0  4
    ## 13 Con8   #3/6/2/2/95-3   NA   NA  20  7  0  7
    ## 14 Mod7             #59 17.0 33.4  19  8  0  5
    ## 15 Mod7            #103 21.4 42.1  19  9  1  9
    ## 16 Mod7       #1/82/3-2   NA   NA  19  6  0  6
    ## 17 Mod7       #3/83/3-2   NA   NA  19  8  0  8
    ## 18 Mod7       #2/95/2-2   NA   NA  20  7  0  7
    ## 19 Mod7       #3/82/3-2 28.0 45.9  20  5  0  5
    ## 20 Mod7       #4/2/95/2 23.5   NA  19  9  0  7
    ## 21 Mod7     #5/3/83/5-2 22.6 37.0  19  5  0  5
    ## 22 Mod7      #8/110/3-2   NA   NA  20  9  0  9
    ## 23 Mod7            #106 21.7 37.8  20  5  0  2
    ## 24 Mod7           #94/2 24.4 42.9  19  7  1  3
    ## 25 Mod7             #62 19.5 35.9  19  7  2  4
    ## 26 Low7           #84/2 24.3 40.8  20  8  0  8
    ## 27 Low7            #107 22.6 42.4  20  9  0  8
    ## 28 Low7           #85/2 22.2 38.5  20  8  0  6
    ## 29 Low7             #98 23.8 43.8  20  9  0  9
    ## 30 Low7            #102 22.6 43.3  20 11  0  7
    ## 31 Low7            #101 23.8 42.7  20  9  0  9
    ## 32 Low7            #111 25.5 44.6  20  3  2  3
    ## 33 Low7            #112 23.9 40.5  19  6  1  1
    ## 34 Mod8             #97 24.5 42.8  20  8  1  8
    ## 35 Mod8           #5/93   NA 41.1  20 11  0  9
    ## 36 Mod8         #5/93/2   NA   NA  19  8  0  8
    ## 37 Mod8       #7/82-3-2 26.9 43.2  20  7  0  7
    ## 38 Mod8      #7/110/3-2 27.5 46.0  19  8  1  8
    ## 39 Mod8         #2/95/2 28.5 44.5  20  9  0  9
    ## 40 Mod8           #82/4 33.4 52.7  20  8  0  6
    ## 41 Low8             #53 21.8 37.2  20  8  1  7
    ## 42 Low8             #79 25.4 43.8  19  8  0  7
    ## 43 Low8            #100 20.0 39.2  20  8  0  7
    ## 44 Low8           #4/84 21.8 35.2  20  4  0  4
    ## 45 Low8            #108 25.6 47.5  20  8  0  7
    ## 46 Low8             #99 23.5 39.0  20  6  0  5
    ## 47 Low8            #110 25.5 42.7  20  7  0  6

## Other file formats

We need to read in excel spreadsheet ….

``` r
mlb_df = read_excel("data/mlb11.xlsx")
```

``` r
View(mlb_df)
```

``` r
lotr_words_df = 
  read_excel(
    "data/mlb11.xlsx", 
    range = "B3:D6"
  )
```

## Still more formats …

Read in a SAS dataset.

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

## Data export

``` r
write_csv(lotr_words_df, file = "data/lotr_words_df.csv")
```

## Why not base r???

``` r
dont_do_this_df = read.csv("data/FAS_litters.csv")
```

## .gitignore –\> data/lotr_words_df.csv
