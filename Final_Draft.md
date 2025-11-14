Final_Draft
================
Stephanie Wiegman
2025-11-11

- [ABSTRACT](#abstract)
- [BACKGROUND](#background)
- [QUESTIONS AND HYPOTHESIS](#questions-and-hypothesis)
  - [Question](#question)
  - [Hypothesis](#hypothesis)
  - [Figure 1](#figure-1)
  - [Figure 2](#figure-2)
  - [Figure 3](#figure-3)
- [DISCUSSION](#discussion)
- [CONCLUSION](#conclusion)
- [REFERENCES](#references)

# ABSTRACT

# BACKGROUND

Citizens have the power to help scientific observations move along. The
widespread ability to collect datad is amazing. Using their observations
of fireflies across Utah we have the opportunity to monitor the firefly
population across the years. This dataset includes retroactive data from
before 2000, however, by focusing on the innformation in the recent
years we can determine trends in the firefly population.

drought? Factors that may influence it? Research on firefly conditions
for habitat

# QUESTIONS AND HYPOTHESIS

## Question

How are the sightings of fireflies and their abundance impacted by month
and yearly conditions?

## Hypothesis

We will see a \## Prediction We will see a common trend of when firefly
activity/population peaks each month. We will see limited variation by
year as their activity may not be reactive to the weather trends. \#
METHODS unfinished Using a data set of firefly observations from Logan’s
citizen science data, we could extract sighting dates, locations, and
habitat type. The number sighted were concluded to be inconsistent
results as many were estimated numbers and could be very easily skewed
by perspective. Therefore, in this study we focused on the instance
report. Counting how many times per month/year fireflies were observed.
Using the ggplot2 package in R would could view how these trends differ
over years. using xxx we can quantify how differnt they are. ADD MORE
HERE

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

![](Final_Draft_files/figure-gfm/figure%202-1.png)<!-- -->

``` r
#Edited with AI to implement/ fix these functions.
```

## Figure 2

``` r
#make plot of Max Julian day
table_Julian <- table(data$Year, data$Julian)
#find the max count each year
max_col <- apply(table_Julian, 1, which.max) 
# create a data frame with year and max julian day
numb_Julian <- as.numeric(colnames(table_Julian)[max_col])
numb_year <- c(2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023, 2024)
#plot as scatter plot
plot(numb_year, numb_Julian)
```

![](Final_Draft_files/figure-gfm/table%20of%20percentages/analysis-1.png)<!-- -->

## Figure 3

``` r
#create data frame 
Julian_dataframe <- data.frame(ColumnA = numb_Julian, ColumnB = numb_year)
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

# CONCLUSION

# REFERENCES

Citizen Science Libraries. (n.d.). UtahFireflies. Google Docs. Retrieved
October 30, 2025, from
<https://docs.google.com/spreadsheets/d/1XLklQd6P3d9wYnmh-3KgzNvP8GfQHL2Y2IyaZMwIOzk/edit?usp=drive_web&ouid=106039106225729317949&usp=embed_facebook>

OpenAI. (2025, October 30). Barplot creation in R \[Generative AI
chat\]. ChatGPT.
