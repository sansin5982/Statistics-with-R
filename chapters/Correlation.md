<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Correlation Analysis

## Introduction

A *correlation analysis* is a statistical method used to examine the
strength and direction of the relationship between two continuous
variables.

### Pearson Correlation Calculation

The Pearson correlation coefficient is calculated using:

$$
\large r = \frac{\sum (x\_i - \bar{x}) (y\_i - \bar{y})}{\sqrt{\sum (x\_i - \bar{x})^2 \sum (y\_i - \bar{y})^2}}
$$

where:

-   *x*<sub>*i*</sub> and *y*<sub>*i*</sub> are the individual sample
    points.
-   *x̄* and *ȳ* are means of *x* and *y*.
-   ∑(*x*<sub>*i*</sub> − *x̄*) ∑(*y*<sub>*i*</sub> − *ȳ*) is the
    cross-product of deviations.
-   ∑(*x*<sub>*i*</sub> − *x̄*)<sup>2</sup> and (y\_i - {y})^2 are the
    sum of of squared deviations.

The most commonly used correlation coefficient is **Pearson’s
correlation coefficient**, which measures the linear relationship
between two variables. Pearson’s correlation coefficient, denoted by
“r,” takes on values between -1 and 1, where a value of -1 indicates a
perfect negative correlation, a value of 0 indicates no correlation, and
a value of 1 indicates a perfect positive correlation.

$$
\large -1 \leq r \leq 1
$$

where:

-   *r* = −1 indicates a perfect negative correlation,
-   *r* = 0 indicates no correlation,
-   *r* = 1 indicates a perfect positive correlation.

To perform a correlation analysis, we first must collect data on the two
variables of interest. Once we have the data, we can calculate the
correlation coefficient using R.

For example, suppose we want to examine the relationship between a
person’s age and their cholesterol level. We collect data on 100
individuals and obtained the following data:

## Example Dataset

We will examine the relationship between a person’s age and their
cholesterol level using sample data:

    # Load necessary libraries
    library(ggplot2)

    # Create age and cholesterol vectors
    age <- c(45, 38, 52, 60, 35, 42, 48, 55, 50, 47)
    cholesterol <- c(210, 185, 240, 250, 175, 200, 220, 235, 230, 210)

    # Combine the vectors into a dataframe
    mydata <- data.frame(age = age, cholesterol = cholesterol)

### Data Representation

<table>
<thead>
<tr class="header">
<th style="text-align: right;">age</th>
<th style="text-align: right;">cholesterol</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">45</td>
<td style="text-align: right;">210</td>
</tr>
<tr class="even">
<td style="text-align: right;">38</td>
<td style="text-align: right;">185</td>
</tr>
<tr class="odd">
<td style="text-align: right;">52</td>
<td style="text-align: right;">240</td>
</tr>
<tr class="even">
<td style="text-align: right;">60</td>
<td style="text-align: right;">250</td>
</tr>
<tr class="odd">
<td style="text-align: right;">35</td>
<td style="text-align: right;">175</td>
</tr>
<tr class="even">
<td style="text-align: right;">42</td>
<td style="text-align: right;">200</td>
</tr>
<tr class="odd">
<td style="text-align: right;">48</td>
<td style="text-align: right;">220</td>
</tr>
<tr class="even">
<td style="text-align: right;">55</td>
<td style="text-align: right;">235</td>
</tr>
<tr class="odd">
<td style="text-align: right;">50</td>
<td style="text-align: right;">230</td>
</tr>
<tr class="even">
<td style="text-align: right;">47</td>
<td style="text-align: right;">210</td>
</tr>
</tbody>
</table>

## Scatter Plot

    ggplot(mydata, aes(x = age, y = cholesterol)) + 
      geom_point(color = "blue", size = 3) + 
      geom_smooth(method = "lm", col = "red") +
      labs(title = "Relationship between Age and Cholesterol", x = "Age", y = "Cholesterol") +
      theme_classic()

    ## `geom_smooth()` using formula = 'y ~ x'

![](Correlation_files/figure-markdown_strict/unnamed-chunk-3-1.png)

## Assumptions of Pearson Correlation

### 1. Normality Check

#### Histogram of Age

    ggplot(mydata, aes(x = age)) +
      geom_histogram(binwidth = 5, fill = "lightblue", color = "black") +
      labs(title = "Histogram of Age", x = "Age", y = "Frequency") +
      theme_classic()

![](Correlation_files/figure-markdown_strict/unnamed-chunk-4-1.png)

#### Histogram of Cholesterol

    ggplot(mydata, aes(x = cholesterol)) +
      geom_histogram(binwidth = 20, fill = "lightblue", color = "black") +
      labs(title = "Histogram of Cholesterol", x = "Cholesterol", y = "Frequency") +
      theme_classic()

![](Correlation_files/figure-markdown_strict/unnamed-chunk-5-1.png)

### Shapiro-Wilk Test

The Shapiro-Wilk test is a statistical test used to check the normality
assumption of a population or a sample. It was developed by Samuel
Shapiro and Martin Wilk in 1965.

The null hypothesis of the Shapiro-Wilk test is that the population is
normally distributed. The alternative hypothesis is that the population
is not normally distributed.

The test is based on the correlation between the data and the normal
probability plot (also known as the normal quantile plot). The normal
probability plot is a graphical method to check the normality
assumption. It plots the observed data against the expected values from
a normal distribution. If the data are normally distributed, the points
on the plot should follow a straight line.

The Shapiro-Wilk test is widely used in many fields, such as psychology,
biology, economics, and finance, to check the normality assumption
before applying parametric statistical methods that assume normality,
such as t-tests and ANOVA.

There are several alternative tests that can be used to assess normality
assumptions, depending on the type of data and the research question.
Here are a few examples: Anderson-Darling test, Kolmogorov-Smirnov test,
Normal probability plots, etc

#### Shapiro-Wilk Test for Normality

    shapiro.test(mydata$age) 

    ## 
    ##  Shapiro-Wilk normality test
    ## 
    ## data:  mydata$age
    ## W = 0.99077, p-value = 0.9977

    shapiro.test(mydata$cholesterol)

    ## 
    ##  Shapiro-Wilk normality test
    ## 
    ## data:  mydata$cholesterol
    ## W = 0.96909, p-value = 0.8823

### 2. Linearity Check

    ggplot(mydata, aes(x = age, y = cholesterol)) + 
      geom_point(color = "blue", size = 3) + 
      geom_smooth(method = "lm", col = "red") +
      labs(title = "Linearity Check", x = "Age", y = "Cholesterol") +
      theme_classic()

    ## `geom_smooth()` using formula = 'y ~ x'

![](Correlation_files/figure-markdown_strict/unnamed-chunk-7-1.png)

<table>
<thead>
<tr class="header">
<th style="text-align: right;">age</th>
<th style="text-align: right;">cholesterol</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">45</td>
<td style="text-align: right;">210</td>
</tr>
<tr class="even">
<td style="text-align: right;">38</td>
<td style="text-align: right;">185</td>
</tr>
<tr class="odd">
<td style="text-align: right;">52</td>
<td style="text-align: right;">240</td>
</tr>
<tr class="even">
<td style="text-align: right;">60</td>
<td style="text-align: right;">250</td>
</tr>
<tr class="odd">
<td style="text-align: right;">35</td>
<td style="text-align: right;">175</td>
</tr>
<tr class="even">
<td style="text-align: right;">42</td>
<td style="text-align: right;">200</td>
</tr>
<tr class="odd">
<td style="text-align: right;">48</td>
<td style="text-align: right;">220</td>
</tr>
<tr class="even">
<td style="text-align: right;">55</td>
<td style="text-align: right;">235</td>
</tr>
<tr class="odd">
<td style="text-align: right;">50</td>
<td style="text-align: right;">230</td>
</tr>
<tr class="even">
<td style="text-align: right;">47</td>
<td style="text-align: right;">210</td>
</tr>
</tbody>
</table>

**Step 1: Compute the Means**

The mean of a dataset is calculated as:

$$
\bar{x} = \frac{\sum x\_i}{n}, \quad \bar{y} = \frac{\sum y\_i}{n}
$$

For our dataset:

$$
\bar{x} = \frac{45+38+52+60+35+42+48+55+50+47}{10} = \frac{472}{10} = 47.2
$$

$$
\bar{y} = \frac{210+185+240+250+175+200+220+235+230+210}{10} = \frac{2155}{10} = 215.5
$$
—

**Step 2: Compute Deviations and Squared Deviations**

<table>
<colgroup>
<col style="width: 11%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 15%" />
<col style="width: 15%" />
<col style="width: 18%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Age (<span
class="math inline"><em>x</em><sub><em>i</em></sub></span>)</th>
<th style="text-align: left;">Cholesterol (<span
class="math inline"><em>y</em><sub><em>i</em></sub></span>)</th>
<th style="text-align: left;"><span
class="math inline"><em>x</em><sub><em>i</em></sub> − <em>x̄</em></span></th>
<th style="text-align: left;"><span
class="math inline"><em>y</em><sub><em>i</em></sub> − <em>ȳ</em></span></th>
<th style="text-align: left;"><span
class="math inline">(<em>x</em><sub><em>i</em></sub> − <em>x̄</em>)<sup>2</sup></span></th>
<th style="text-align: left;"><span
class="math inline">(<em>y</em><sub><em>i</em></sub> − <em>ȳ</em>)<sup>2</sup></span></th>
<th style="text-align: left;"><span
class="math inline">(<em>x</em><sub><em>i</em></sub> − <em>x̄</em>)(<em>y</em><sub><em>i</em></sub> − <em>ȳ</em>)</span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">45</td>
<td style="text-align: left;">210</td>
<td style="text-align: left;">-2.2</td>
<td style="text-align: left;">-5.5</td>
<td style="text-align: left;">4.84</td>
<td style="text-align: left;">30.25</td>
<td style="text-align: left;">12.1</td>
</tr>
<tr class="even">
<td style="text-align: left;">38</td>
<td style="text-align: left;">185</td>
<td style="text-align: left;">-9.2</td>
<td style="text-align: left;">-30.5</td>
<td style="text-align: left;">84.64</td>
<td style="text-align: left;">930.25</td>
<td style="text-align: left;">280.6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">52</td>
<td style="text-align: left;">240</td>
<td style="text-align: left;">4.8</td>
<td style="text-align: left;">24.5</td>
<td style="text-align: left;">23.04</td>
<td style="text-align: left;">600.25</td>
<td style="text-align: left;">117.6</td>
</tr>
<tr class="even">
<td style="text-align: left;">60</td>
<td style="text-align: left;">250</td>
<td style="text-align: left;">12.8</td>
<td style="text-align: left;">34.5</td>
<td style="text-align: left;">163.84</td>
<td style="text-align: left;">1190.25</td>
<td style="text-align: left;">441.6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">35</td>
<td style="text-align: left;">175</td>
<td style="text-align: left;">-12.2</td>
<td style="text-align: left;">-40.5</td>
<td style="text-align: left;">148.84</td>
<td style="text-align: left;">1640.25</td>
<td style="text-align: left;">494.1</td>
</tr>
<tr class="even">
<td style="text-align: left;">42</td>
<td style="text-align: left;">200</td>
<td style="text-align: left;">-5.2</td>
<td style="text-align: left;">-15.5</td>
<td style="text-align: left;">27.04</td>
<td style="text-align: left;">240.25</td>
<td style="text-align: left;">80.6</td>
</tr>
<tr class="odd">
<td style="text-align: left;">48</td>
<td style="text-align: left;">220</td>
<td style="text-align: left;">0.8</td>
<td style="text-align: left;">4.5</td>
<td style="text-align: left;">0.64</td>
<td style="text-align: left;">20.25</td>
<td style="text-align: left;">3.6</td>
</tr>
<tr class="even">
<td style="text-align: left;">55</td>
<td style="text-align: left;">235</td>
<td style="text-align: left;">7.8</td>
<td style="text-align: left;">19.5</td>
<td style="text-align: left;">60.84</td>
<td style="text-align: left;">380.25</td>
<td style="text-align: left;">152.1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">50</td>
<td style="text-align: left;">230</td>
<td style="text-align: left;">2.8</td>
<td style="text-align: left;">14.5</td>
<td style="text-align: left;">7.84</td>
<td style="text-align: left;">210.25</td>
<td style="text-align: left;">40.6</td>
</tr>
<tr class="even">
<td style="text-align: left;">47</td>
<td style="text-align: left;">210</td>
<td style="text-align: left;">-0.2</td>
<td style="text-align: left;">-5.5</td>
<td style="text-align: left;">0.04</td>
<td style="text-align: left;">30.25</td>
<td style="text-align: left;">1.1</td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

**Step 3: Compute Summations**

∑(*x*<sub>*i*</sub> − *x̄*)(*y*<sub>*i*</sub> − *ȳ*) = 1624.3

∑(*x*<sub>*i*</sub> − *x̄*)<sup>2</sup> = 521.76

∑(*y*<sub>*i*</sub> − *ȳ*)<sup>2</sup> = 5272.5

------------------------------------------------------------------------

**Step 4: Compute Pearson Correlation Coefficient**

The Pearson correlation coefficient is calculated as:

$$
r = \frac{\sum (x\_i - \bar{x}) (y\_i - \bar{y})}{\sqrt{\sum (x\_i - \bar{x})^2 \sum (y\_i - \bar{y})^2}}
$$

Substituting values:

$$
r = \frac{1624.3}{\sqrt{521.76 \times 5272.5}}
$$

$$
r = \frac{1624.3}{\sqrt{2751143.6}}
$$

$$
r = \frac{1624.3}{1658.6}
$$

*r* = 0.98

------------------------------------------------------------------------

**Step 5: Statistical Significance Test**

We test the null hypothesis:

*H*<sub>0</sub> : There is no correlation  (*r* = 0)

The test statistic is calculated using:

$$
t = \frac{r \sqrt{n-2}}{\sqrt{1 - r^2}}
$$

Substituting values:

$$
t = \frac{0.98 \times \sqrt{10-2}}{\sqrt{1 - 0.98^2}}
$$

$$
t = \frac{0.98 \times \sqrt{8}}{\sqrt{1 - 0.9604}}
$$

$$
t = \frac{0.98 \times 2.83}{\sqrt{0.0396}}
$$

$$
t = \frac{2.77}{0.199}
$$

*t* = 13.94

-   The degrees of freedom (df) for Pearson correlation significance
    testing is calculated using the formula:

-   df = n - 2

where: \* n is the number of observations in the dataset.

-   The Pearson correlation formula includes **two estimated means**
    (*x̄* and *ȳ*, which reduces the independent data points available
    for variability estimation.
-   The correlation coefficient relies on **bivariate relationships**,
    and removing **two degrees of freedom** accounts for the constraints
    imposed by using means in the calculations.

Using a **t-distribution table for 8 degrees of freedom** at *α* = 0.05:

*t*<sub>*c**r**i**t**i**c**a**l*</sub> = 2.306

Since *t* = 13.94 &gt; 2.306, we **reject** *H*<sub>0</sub> and conclude
that the correlation is **statistically significant**.

**Performing Pearson Correlation in R**

    cor(mydata$age, mydata$cholesterol)

    ## [1] 0.9792846

### Statistical Significance Test

    cor.test(mydata$age, mydata$cholesterol)

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  mydata$age and mydata$cholesterol
    ## t = 13.679, df = 8, p-value = 7.858e-07
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  0.9119540 0.9952539
    ## sample estimates:
    ##       cor 
    ## 0.9792846

## Spearman Rank Correlation

The spearman rank correlation is a non-parametric statistical method
used to measure the strength and direction of the association between
two variables. It is calculated by ranking the values of each variable
and calculating the correlation coefficient between their ranks. It is
robust to outliers and can be used with ordinal or non-normally
distributed data.

Let’s say we want to investigate the relationship between the amount of
hours that students spend studying for a test and their corresponding
test scores. We collect data from 10 students and get the following
results:

$$
\rho = 1 - \frac{6 \sum d\_i^2}{n(n^2 - 1)}
$$

where:

-   *d*<sub>*i*</sub> = difference between ranks of corresponding
    values.
-   *n* = number of observations.
-   ∑*d*<sub>*i*</sub><sup>2</sup> = sum of squared rank differences.

------------------------------------------------------------------------

**Step 1: Given Dataset**

<table>
<thead>
<tr class="header">
<th>Hours Studied (<span class="math inline"><em>x</em></span>)</th>
<th>Test Score (<span class="math inline"><em>y</em></span>)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>2</td>
<td>60</td>
</tr>
<tr class="even">
<td>3</td>
<td>70</td>
</tr>
<tr class="odd">
<td>5</td>
<td>80</td>
</tr>
<tr class="even">
<td>6</td>
<td>85</td>
</tr>
<tr class="odd">
<td>7</td>
<td>90</td>
</tr>
<tr class="even">
<td>8</td>
<td>95</td>
</tr>
<tr class="odd">
<td>9</td>
<td>98</td>
</tr>
<tr class="even">
<td>10</td>
<td>100</td>
</tr>
<tr class="odd">
<td>12</td>
<td>99</td>
</tr>
<tr class="even">
<td>14</td>
<td>95</td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

**Step 2: Assign Ranks**

We rank both variables from lowest to highest.

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 22%" />
<col style="width: 25%" />
<col style="width: 22%" />
</colgroup>
<thead>
<tr class="header">
<th>Hours Studied (<span
class="math inline"><em>x</em><sub><em>i</em></sub></span>)</th>
<th>Rank (<span
class="math inline"><em>R</em><sub><em>x</em></sub></span>)</th>
<th>Test Score (<span
class="math inline"><em>y</em><sub><em>i</em></sub></span>)</th>
<th>Rank (<span
class="math inline"><em>R</em><sub><em>y</em></sub></span>)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>2</td>
<td>1</td>
<td>60</td>
<td>1</td>
</tr>
<tr class="even">
<td>3</td>
<td>2</td>
<td>70</td>
<td>2</td>
</tr>
<tr class="odd">
<td>5</td>
<td>3</td>
<td>80</td>
<td>3</td>
</tr>
<tr class="even">
<td>6</td>
<td>4</td>
<td>85</td>
<td>4</td>
</tr>
<tr class="odd">
<td>7</td>
<td>5</td>
<td>90</td>
<td>5</td>
</tr>
<tr class="even">
<td>8</td>
<td>6</td>
<td>95</td>
<td>7</td>
</tr>
<tr class="odd">
<td>9</td>
<td>7</td>
<td>98</td>
<td>8</td>
</tr>
<tr class="even">
<td>10</td>
<td>8</td>
<td>100</td>
<td>9</td>
</tr>
<tr class="odd">
<td>12</td>
<td>9</td>
<td>99</td>
<td>10</td>
</tr>
<tr class="even">
<td>14</td>
<td>10</td>
<td>95</td>
<td>6</td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

**Step 3: Compute Rank Differences and Squared Differences**

The difference in ranks is:

*d*<sub>*i*</sub> = *R*<sub>*x*</sub> − *R*<sub>*y*</sub>

The squared difference is:

*d*<sub>*i*</sub><sup>2</sup> = (*R*<sub>*x*</sub> − *R*<sub>*y*</sub>)<sup>2</sup>

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 18%" />
<col style="width: 21%" />
<col style="width: 18%" />
<col style="width: 7%" />
<col style="width: 7%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Hours Studied (<span
class="math inline"><em>x</em><sub><em>i</em></sub></span>)</th>
<th style="text-align: left;">Rank (<span
class="math inline"><em>R</em><sub><em>x</em></sub></span>)</th>
<th style="text-align: left;">Test Score (<span
class="math inline"><em>y</em><sub><em>i</em></sub></span>)</th>
<th style="text-align: left;">Rank (<span
class="math inline"><em>R</em><sub><em>y</em></sub></span>)</th>
<th style="text-align: left;"><span
class="math inline"><em>d</em><sub><em>i</em></sub></span></th>
<th style="text-align: left;"><span
class="math inline"><em>d</em><sub><em>i</em></sub><sup>2</sup></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">2</td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">60</td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">0</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="even">
<td style="text-align: left;">3</td>
<td style="text-align: left;">2</td>
<td style="text-align: left;">70</td>
<td style="text-align: left;">2</td>
<td style="text-align: left;">0</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="odd">
<td style="text-align: left;">5</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">80</td>
<td style="text-align: left;">3</td>
<td style="text-align: left;">0</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="even">
<td style="text-align: left;">6</td>
<td style="text-align: left;">4</td>
<td style="text-align: left;">85</td>
<td style="text-align: left;">4</td>
<td style="text-align: left;">0</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="odd">
<td style="text-align: left;">7</td>
<td style="text-align: left;">5</td>
<td style="text-align: left;">90</td>
<td style="text-align: left;">5</td>
<td style="text-align: left;">0</td>
<td style="text-align: left;">0</td>
</tr>
<tr class="even">
<td style="text-align: left;">8</td>
<td style="text-align: left;">6</td>
<td style="text-align: left;">95</td>
<td style="text-align: left;">7</td>
<td style="text-align: left;">-1</td>
<td style="text-align: left;">1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">9</td>
<td style="text-align: left;">7</td>
<td style="text-align: left;">98</td>
<td style="text-align: left;">8</td>
<td style="text-align: left;">-1</td>
<td style="text-align: left;">1</td>
</tr>
<tr class="even">
<td style="text-align: left;">10</td>
<td style="text-align: left;">8</td>
<td style="text-align: left;">100</td>
<td style="text-align: left;">9</td>
<td style="text-align: left;">-1</td>
<td style="text-align: left;">1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">12</td>
<td style="text-align: left;">9</td>
<td style="text-align: left;">99</td>
<td style="text-align: left;">10</td>
<td style="text-align: left;">-1</td>
<td style="text-align: left;">1</td>
</tr>
<tr class="even">
<td style="text-align: left;">14</td>
<td style="text-align: left;">10</td>
<td style="text-align: left;">95</td>
<td style="text-align: left;">6</td>
<td style="text-align: left;">4</td>
<td style="text-align: left;">16</td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

## **Step 4: Compute Summation**

∑*d*<sub>*i*</sub><sup>2</sup> = 0 + 0 + 0 + 0 + 0 + 1 + 1 + 1 + 1 + 16 = 20

------------------------------------------------------------------------

## **Step 5: Compute Spearman Correlation**

Using the formula:

$$
\rho = 1 - \frac{6 \sum d\_i^2}{n(n^2 - 1)}
$$

Substituting values:

$$
\rho = 1 - \frac{6 \times 20}{10(10^2 - 1)}
$$

$$
\rho = 1 - \frac{120}{10(100 - 1)}
$$

$$
\rho = 1 - \frac{120}{10 \times 99}
$$

$$
\rho = 1 - \frac{120}{990}
$$

*ρ* = 1 − 0.1212

*ρ* = 0.8788

------------------------------------------------------------------------

**Step 6: Statistical Significance Test**

We test the null hypothesis:

*H*<sub>0</sub> : There is no correlation  (*ρ* = 0)

The test statistic is:

$$
t = \frac{\rho \sqrt{n - 2}}{\sqrt{1 - \rho^2}}
$$

Substituting values:

$$
t = \frac{0.8788 \times \sqrt{10-2}}{\sqrt{1 - 0.8788^2}}
$$

$$
t = \frac{0.8788 \times \sqrt{8}}{\sqrt{1 - 0.7722}}
$$

$$
t = \frac{0.8788 \times 2.83}{\sqrt{0.2278}}
$$

$$
t = \frac{2.487}{0.4773}
$$

*t* = 5.21

Using a **t-distribution table for 8 degrees of freedom** at *α* = 0.05:

*t*<sub>*c**r**i**t**i**c**a**l*</sub> = 2.306

Since *t* = 5.21 &gt; 2.306, we **reject** *H*<sub>0</sub> and conclude
that the correlation is **statistically significant**.

------------------------------------------------------------------------

### Spearman Correlation Calculation using R

    cor.test(mydata$Hr_St, mydata$Test_score, method = "spearman")

    ## Warning in cor.test.default(mydata$Hr_St, mydata$Test_score, method =
    ## "spearman"): Cannot compute exact p-value with ties

    ## 
    ##  Spearman's rank correlation rho
    ## 
    ## data:  mydata$Hr_St and mydata$Test_score
    ## S = 17.553, p-value = 0.0004919
    ## alternative hypothesis: true rho is not equal to 0
    ## sample estimates:
    ##       rho 
    ## 0.8936211

## Conclusion

-   Pearson’s correlation coefficient is used for linear relationships
    assuming normality.
-   Spearman’s correlation is robust to non-normal distributions and
    outliers.
-   The results indicate a **strong positive correlation** in both
    cases, implying a significant association between the variables.

#### References

1.  Pearson, K. (1895). “Notes on Regression and Inheritance in the Case
    of Two Parents.” *Proceedings of the Royal Society of London*,
    58(1), 240–242.
2.  Spearman, C. (1904). “The Proof and Measurement of Association
    between Two Things.” *The American Journal of Psychology*, 15(1),
    72–101.
3.  Shapiro, S. S., & Wilk, M. B. (1965). “An Analysis of Variance Test
    for Normality (Complete Samples).” *Biometrika*, 52(3-4), 591–611.
4.  Cohen, J. (1988). *Statistical Power Analysis for the Behavioral
    Sciences*. Routledge.

[⬅ Back to Home](../index.md)
