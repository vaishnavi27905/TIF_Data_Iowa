Here, I am using creating csv data file for the Tax increament finance
(TIF)

``` r
# Load the correct library for Excel files
library(readxl)

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

here I have made graph for Assessment Year, Estimated Revenue (\$
Millions) which can readable and understandable.

``` r
final_plot_data <- TIF_data_Iowa %>%
  filter(!is.na(...1))

ggplot(final_plot_data,
       aes(x = as.numeric(...1),
           y = `Estimated TIF Revenues ($ Millions)`)) +
  geom_line(color = "#2c3e50", linewidth = 1.2) +
  geom_point(color = "#e74c3c", size = 3) +
  theme_minimal() +
  scale_y_continuous(labels = label_dollar()) +
  scale_x_continuous(breaks = seq(2000, 2021, by = 2)) +
  labs(
    title = "Projected TIF Revenues Over Time",
    subtitle = "Iowa Urban Renewal Analysis (2000-2021)",
    x = "Assessment Year",
    y = "Estimated Revenue ($ Millions)",
    caption = "Source: TIF data Iowa"
  ) +
  theme(plot.title = element_text(face = "bold", size = 14))
```

    ## Warning in FUN(X[[i]], ...): NAs introduced by coercion
    ## Warning in FUN(X[[i]], ...): NAs introduced by coercion

    ## Warning: Removed 1 row containing missing values or values outside the scale range
    ## (`geom_line()`).

    ## Warning: Removed 1 row containing missing values or values outside the scale range
    ## (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

can you create the base year graph by compare with each year.

``` r
# Load necessary libraries
library(ggplot2)
library(dplyr)
```

The above graph is count and TIF Estimated Revenues (\$ Millions) with
bar graph.

``` r
# 1. Prepare the dataset (Data sourced from provided tables)
tif_data <- data.frame(
  Year = 1981:2021,
  Count = c(1, 3, 4, 3, 10, 11, 22, 37, 40, 40, 26, 56, 80, 39, 17, 19, 13, 9, 29, 34, 
            38, 70, 46, 38, 35, 46, 56, 56, 53, 76, 65, 87, 72, 71, 88, 81, 102, 107, 109, 89, 8),
  Revenue = c(0.1, 11.7, 2.5, 0.5, 2.6, 5.3, 12.9, 26.9, 19.9, 11.1, 11.2, 28.1, 23.1, 6.1, 1.4, 
              4.2, 4.4, 5.3, 15.3, 14.8, 3.6, 14.9, 6.2, 6.1, 4.0, 10.2, 10.1, 9.6, 7.7, 6.0, 
              5.6, 13.8, 11.6, 11.1, 14.9, 15.1, 13.0, 20.0, 9.0, 2.1, 0.02)
)

# 2. Define the scaling factor for the second axis
# Since Count goes up to ~110 and Revenue to ~30, we multiply Revenue by 4 to align them
scale_factor <- 4

# 3. Create the Dual-Axis Visualization
ggplot(tif_data, aes(x = Year)) +
  # Bar chart for Project Count (Primary Axis)
  geom_bar(aes(y = Count), stat = "identity", fill = "#3498db", alpha = 0.3) +
  # Line chart for TIF Revenue (Scaled to fit the Primary Axis)
  geom_line(aes(y = Revenue * scale_factor), color = "#e74c3c", size = 1) +
  # Formatting the axes
  scale_y_continuous(
    name = "Count",
    sec.axis = sec_axis(~./scale_factor, name = "TIF Estimated Revenues ($ Millions)")
  ) +
  theme_minimal() +
  labs(
    title = "Project Count vs. TIF Revenue (1981-2021)",
    x = "Year"
  ) +
  theme(
    axis.title.y = element_text(color = "#3498db", face = "bold"),
    axis.title.y.right = element_text(color = "#e74c3c", face = "bold"),
    panel.grid.minor = element_blank()
  )
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

![](README_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->
