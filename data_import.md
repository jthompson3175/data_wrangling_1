Data Import
================
Julia Thompson
9/17/2019

## Load in litters dataset

*Read\_csv* makes things a tibble, where *read.csv* makes things a
regular dataframe. They have small differences, and it is arguably
better to use *read\_csv* always.

Also, always use *relative paths* instead of *absolute paths*. This
keeps shit from hitting the fan when you add a folder or move something
etc. Use *getwd()* to find out your working directory, then just use the
last part.

``` r
litters_data = read_csv(file = "./data/FAS_litters.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   Group = col_character(),
    ##   `Litter Number` = col_character(),
    ##   `GD0 weight` = col_double(),
    ##   `GD18 weight` = col_double(),
    ##   `GD of Birth` = col_double(),
    ##   `Pups born alive` = col_double(),
    ##   `Pups dead @ birth` = col_double(),
    ##   `Pups survive` = col_double()
    ## )

``` r
litters_data = janitor::clean_names(litters_data)

# litters_data = read_csv(file = "./data/FAS_litters.csv",
#  skip = 10, col_names = FALSE)

# litters_data = read_csv(
#   file = "./data/FAS_litters.csv",
#   col_types = cols(
#     Group = col_character(),
#     `Litter Number` = col_character(),
#     `GD0 weight` = col_double(),
#     `GD18 weight` = col_double(),
#     `GD of Birth` = col_integer(),
#     `Pups born alive` = col_integer(),
#     `Pups dead @ birth` = col_integer(),
#     `Pups survive` = col_integer()
#   )
# )
```

## Load in pups dataset

``` r
pups_data = read_csv(file = "./data/FAS_pups.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   `Litter Number` = col_character(),
    ##   Sex = col_double(),
    ##   `PD ears` = col_double(),
    ##   `PD eyes` = col_double(),
    ##   `PD pivot` = col_double(),
    ##   `PD walk` = col_double()
    ## )

``` r
pups_data = janitor::clean_names(pups_data)
```

## Read in an excel file

``` r
mlb11_data = read_excel(path = "./data/mlb11.xlsx")

#mlb11_data = read_excel(
#  path = "./data/mlb11.xlsx",
#  sheet = 
#  range = )
```

## Read in a SAS dataset

``` r
pulse_data = haven::read_sas("./data/public_pulse_data.sas7bdat")
```

## Exporting data

``` r
mlb11_data_subset = read_excel(
  path = "./data/mlb11.xlsx",
  range = "A1:D7")

write_csv(mlb11_data_subset, path = "./data/mlb_subset.csv")
```
