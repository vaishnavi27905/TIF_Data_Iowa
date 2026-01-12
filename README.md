Here, I am using creating csv data file for the Tax increament finance
(TIF)

``` r
# Load the correct library for Excel files
library(readxl)
library(readr)

# Use read_excel instead of read_csv for .xlsx files
TIF_data_Iowa <- read_excel("C:/Users/vaish/Downloads/TIF data Iowa.xlsx")
```

    ## New names:
    ## • `` -> `...1`
    ## • `` -> `...2`

``` r
# Now it should show the data table as separate page
View(TIF_data_Iowa)


summary(TIF_data_Iowa)
```

    ##      ...1               ...2           Frozen Base Valuation ($ Millions)
    ##  Length:23          Length:23          Min.   : 6601                     
    ##  Class :character   Class :character   1st Qu.: 7544                     
    ##  Mode  :character   Mode  :character   Median : 8770                     
    ##                                        Mean   : 9124                     
    ##                                        3rd Qu.:10226                     
    ##                                        Max.   :12820                     
    ##                                        NA's   :1                         
    ##  Increment Valuation ($ Millions) Estimated TIF Revenues ($ Millions)
    ##  Min.   : 4463                    Min.   :130.3                      
    ##  1st Qu.: 6970                    1st Qu.:226.6                      
    ##  Median : 8949                    Median :287.5                      
    ##  Mean   : 9116                    Mean   :280.1                      
    ##  3rd Qu.:10972                    3rd Qu.:329.9                      
    ##  Max.   :14691                    Max.   :421.1                      
    ##  NA's   :1                        NA's   :1                          
    ##  Estimated TIF Revenues % Change Over Previous Year
    ##  Min.   :-0.017                                    
    ##  1st Qu.: 0.025                                    
    ##  Median : 0.043                                    
    ##  Mean   : 0.053                                    
    ##  3rd Qu.: 0.068                                    
    ##  Max.   : 0.167                                    
    ##  NA's   :2                                         
    ##  Estimated TIF Revenues Per Capita
    ##  Min.   : 44.49                   
    ##  1st Qu.: 76.30                   
    ##  Median : 93.84                   
    ##  Mean   : 91.06                   
    ##  3rd Qu.:105.39                   
    ##  Max.   :131.70                   
    ##  NA's   :1

``` r
#colnames(TIF_data_Iowa)

#names(TIF_data_Iowa)

#dim(TIF_data_Iowa)

#head(TIF_data_Iowa)

#glimpse(TIF_data_Iowa)
```
