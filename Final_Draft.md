Final_Draft
================
Stephanie Spencer
2025-11-14

- [ABSTRACT](#abstract)
- [BACKGROUND](#background)
- [QUESTIONS AND HYPOTHESIS](#questions-and-hypothesis)
  - [Question](#question)
  - [Hypothesis](#hypothesis)
  - [Figure 1](#figure-1)
  - [Figure 2](#figure-2)
  - [Figure 3](#figure-3)
- [DISCUSSION](#discussion)
  - [Analysis of Figure 1](#analysis-of-figure-1)
  - [Analysis of Figure 2](#analysis-of-figure-2)
  - [Analysis of Figure 3](#analysis-of-figure-3)
- [CONCLUSION](#conclusion)
- [REFERENCES](#references)

# ABSTRACT

# BACKGROUND

Citizens have the power to help scientific observations move along. The
widespread ability to collect data is amazing. Using their observations
of fireflies across Utah we have the opportunity to monitor the firefly
population across the years. This data set includes retroactive data
from before 2000, however, by focusing on the information from 2016 to
2024, we can determine more recent trends in the firefly population. In
Evans et al. paper from 2019 they found a link between the larval stage
abundance and the climate, where the temperature in the prevoius year
would affect the abundance and timing of the next year’s larval stage.
This is an indication that temeprature could be having an effect on the
firefly abundance each year.

# QUESTIONS AND HYPOTHESIS

## Question

How are the sightings of fireflies and their abundance impacted by month
and yearly conditions?

## Hypothesis

We will see a decrease in fireflies each year due to global warming or
other temperature affects. \## Prediction We will see a common trend of
when firefly activity/population peaks each month. We will see limited
variation by year as their activity may not be reactive to the weather
trends. \# METHODS Using a data set of firefly observations from Logan’s
citizen science data, we could extract sighting dates, locations, and
habitat type. The number sighted were concluded to be inconsistent
results as many were estimated numbers and could be very easily skewed
by perspective. Therefore, in this study we focused on the instance
report. Counting how many times per month/year fireflies were observed.
Using the ggplot2 package in R would could view how these trends differ
by month over years. To zoom in more, we can use Julian days of the peak
observation day of each year to show if the fireflies are peaking
earlier or later. This data can be compared with climate/weather data.
To quantify how different each year was, and if there was a linear trend
we used linear modeling and ANOVA test for signifigance.

## Figure 1

``` r
ggplot(data, aes(x = Month)) +
  geom_bar(fill = "yellow3") +
  facet_grid(~ Year) +
  labs(title = "Observations Recorded by Month and Year",
       x = "Month",
       y = "Number of Observations") +
  theme_minimal()
```

![](Final_Draft_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

``` r
#Edited with AI to implement/ fix these functions.
```

## Figure 2

``` r
#make plot of Max Julian day
table_Julian <- table(data$Year, data$Julian)
#find the max count each year
max_col <- apply(table_Julian, 1, which.max) 
# create a data frame with year and max Julian day
Max_Julian_Day <- as.numeric(colnames(table_Julian)[max_col])
years <- c(2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024)
#plot as scatter plot
plot(years, Max_Julian_Day, main = "Peak Days of Observations", xlab = "Year", ylab = "Julain Days")
```

![](Final_Draft_files/figure-gfm/maximum%20Julian%20day-1.png)<!-- -->

## Figure 3

``` r
#create data frame 
Julian_dataframe <- data.frame(ColumnA = Max_Julian_Day, ColumnB = years)
m1 <- lm( ColumnA ~ ColumnB, data=Julian_dataframe)
# run anova test for p value
anova(m1)
```

    ## Analysis of Variance Table
    ## 
    ## Response: ColumnA
    ##           Df Sum Sq Mean Sq F value Pr(>F)
    ## ColumnB    1 135.00  135.00  1.2014 0.3093
    ## Residuals  7 786.56  112.36

``` r
summary(m1)
```

    ## 
    ## Call:
    ## lm(formula = ColumnA ~ ColumnB, data = Julian_dataframe)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -18.278  -2.778  -1.778   7.222  16.222 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)
    ## (Intercept) 3192.778   2764.342   1.155    0.286
    ## ColumnB       -1.500      1.368  -1.096    0.309
    ## 
    ## Residual standard error: 10.6 on 7 degrees of freedom
    ## Multiple R-squared:  0.1465, Adjusted R-squared:  0.02456 
    ## F-statistic: 1.201 on 1 and 7 DF,  p-value: 0.3093

# DISCUSSION

## Analysis of Figure 1

We see a consistency across the 9 years that firefly observations peak
in June each year. The size of the peaks varies, with a seemingly
decreased trend of observations. However, as this data come from citizen
science many factors could impact the numbers including how often people
continue to submit sightings after several years.

## Analysis of Figure 2

## Analysis of Figure 3

# CONCLUSION

# REFERENCES

Citizen Science Libraries. (n.d.). UtahFireflies. Google Docs. Retrieved
October 30, 2025, from
<https://docs.google.com/spreadsheets/d/1XLklQd6P3d9wYnmh-3KgzNvP8GfQHL2Y2IyaZMwIOzk/edit?usp=drive_web&ouid=106039106225729317949&usp=embed_facebook>

Evans, T. R., Salvatore, D., van de Pol, M., & Musters, C. j. m. (2019).
Adult firefly abundance is linked to weather during the larval stage in
the previous year. Ecological Entomology, 44(2), 265–273.
<https://doi.org/10.1111/een.12702>

OpenAI. (2025, October 30). Barplot creation in R \[Generative AI
chat\]. ChatGPT.
