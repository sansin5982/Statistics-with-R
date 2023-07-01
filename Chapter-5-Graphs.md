# Graphs

Graphs play a crucial role in statistics as they help visualize data,
identify patterns, and communicate insights effectively. Here are some
commonly used graphs in statistics:

    library(ggplot2) # for data visualization
    library(MASS)
    library(tidyr)
    library(scales)

### Grammar of graphics

-   2 principals
    -   Graphics = distinct layers of grammatical elements
    -   Meaningful plots through aesthetic mappings

### Essential grammatical elements

-   Data The dataset being plotted
-   Aesthetics The scales onto which we map our data
-   Geometries The visual elements used for our data
-   Facets Plotting small multiples
-   Statistics Representation of our data to aid understanding
-   Coordinates The space on which data will be plotted
-   Themes All non-data ink

## Bar Chart

A bar chart displays the distribution of categorical or discrete data.
It consists of bars, where the height represents the frequency or
proportion of each category. Bar charts are useful for comparing
categories and identifying the most common or least common ones.

-   We are using mtcars dataset
-   Before doing visualization a basic exploration of data is must

<!-- -->

    head(mtcars) # first 6 observations

    ##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1

    str(mtcars) # structure of all variables

    ## 'data.frame':    32 obs. of  11 variables:
    ##  $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
    ##  $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
    ##  $ disp: num  160 160 108 258 360 ...
    ##  $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
    ##  $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
    ##  $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
    ##  $ qsec: num  16.5 17 18.6 19.4 17 ...
    ##  $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
    ##  $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
    ##  $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
    ##  $ carb: num  4 4 1 1 2 1 4 2 2 4 ...

-   Some columns are read as numeric, however, they are categorical.
    Hence, we have to convert them into factors first

<!-- -->

    # # Convert 'vs' column to factor
    # mtcars$vs <- factor(mtcars$vs)
    # 
    # # Convert 'am' column to factor
    # mtcars$am <- factor(mtcars$am)
    # 
    # # Convert 'gear' column to factor
    # mtcars$gear <- factor(mtcars$gear)

    str(mtcars)

    ## 'data.frame':    32 obs. of  11 variables:
    ##  $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
    ##  $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
    ##  $ disp: num  160 160 108 258 360 ...
    ##  $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
    ##  $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
    ##  $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
    ##  $ qsec: num  16.5 17 18.6 19.4 17 ...
    ##  $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
    ##  $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
    ##  $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
    ##  $ carb: num  4 4 1 1 2 1 4 2 2 4 ...

    table(mtcars$cyl)

    ## 
    ##  4  6  8 
    ## 11  7 14

    ggplot(mtcars, aes(x = factor(cyl))) +
     geom_bar()

![](Chapter-5-Graphs_files/figure-markdown_strict/unnamed-chunk-7-1.png)

## Pie Chart

A pie chart represents the composition of a whole in terms of its parts.
It is a circular graph where each slice (or sector) represents a
category, and the angle of the slice corresponds to the proportion of
that category. Pie charts are useful for displaying proportions and
relative contributions of different categories.

## Histogram

A histogram displays the distribution of continuous or discrete data. It
consists of bars where the height represents the frequency or proportion
of data falling within each interval. Histograms help identify the shape
(e.g., symmetric, skewed), central tendency, and variability of a
dataset.

## Frequency Polygon

## Density plot

## Stem and Leaf plot

## Box plot

A box plot, also known as a box-and-whisker plot, provides a visual
summary of the distribution of continuous data. It displays the median,
quartiles, and outliers of the dataset. Box plots are useful for
comparing distributions, identifying skewness, and detecting potential
outliers.

## Scatter plot

A scatter plot shows the relationship between two continuous variables.
Each data point is represented as a point on the graph, allowing for the
identification of patterns, trends, and the strength of the association
between the variables. Scatter plots are commonly used in correlation
analysis.

## Bubble plot

## Line Chart

A line chart displays the relationship between two continuous variables
over time or any other ordered variable. It shows the trend, patterns,
and changes in the data over a specific period. Line charts are commonly
used in time series analysis and tracking variables over time.
