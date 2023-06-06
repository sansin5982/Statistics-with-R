# Numerical measures

Numerical measures are summary statistics that are used to describe the
characteristics of a dataset. They provide information about the central
tendency, variability, and distribution of the data.

## Measures of Central Tendency

Measures of central tendency are numerical measures that describe the
center of a dataset. The three commonly used measures of central
tendency are:

### Mean

-   The mean is the arithmetic average of a dataset.
-   It is calculated by summing all the values in the dataset and
    dividing by the number of observations.
-   The mean is a good measure of central tendency for datasets that are
    **normally distributed or approximately symmetric**.
-   However, the **mean can be influenced by outliers and extreme
    values**, which can skew the results.

**Sample mean calculation**
$$\huge\overline{x}=\frac{1}{n}\sum\_\\ xi$$

-   ∑ = Summation (Adding all observations)
-   n = Number of observations
-   xi = Individual observation
-   $\overline{x}$ = sample mean

**Population mean calculation**
$$\huge\mu=\frac{1}{N}\sum\_\\ xi$$

-   ∑ = Summation (Adding all observations)
-   n = Number of observations
-   xi = Individual observation
-   *μ* = Population mean

Example: Find the mean of the set {5, 1, 3, 7, 9}.

-   Total number of observation is 5. Hence, n is 5
-   Summation of all observation is (5 + 1 + 3 + 7 + 9) = 25
-   Mean = 25/5 = 5

**Hands-On in R**

Suppose we have a vector of numbers representing the test scores of a
group of students:

    test_scores <- c(85, 72, 90, 68, 93, 80, 77, 88)

To calculate the mean of these test scores in R, we can use the `mean()`
function:

-Syntax: `mean(x, na.rm = FALSE)`

na.rm is used to remove the missing values from the input vector.

    mean_score <- mean(test_scores)
    print(mean_score)

    ## [1] 81.625

Therefore, the mean test score of these students is 81.625.

### Median

-   The median is the middle value in a dataset when the values are
    arranged in order.
-   It is **less sensitive to outliers than the mean** and is a good
    measure of central tendency for datasets that are skewed or have
    outliers.
-   The median divides the dataset into two equal parts, with 50% of the
    observations above and 50% below the median.
-   Calculation of median also depends on if the observations are odd or
    even.

**ODD number of observations**: - Arrange the observations from smallest
to largest number. - To calculate median value for odd number of
observation, we have to identify middle location. - Observation located
at middle location is will be considered as median value.

$$\huge \frac{n + 1}{2} observation$$
 - n = Number of observations

Example: Find the median of the set {5, 1, 3, 7, 9}.

1.  Arrange the numbers in order: {1, 3, 5, 7, 9}.
2.  Identify the middle number: Total number of observation is 5. Hence,
    (5+1)/2 is 3. It means value located at 3rd observation is median
    value.
3.  Hence, 5 is the median value. Therefore, the median of the set {5,
    1, 3, 7, 9} is 5.

**Even number of observations**: - Arrange the observations from
smallest to largest number. - To calculate median value for even number
of observation, we have to identify middle location, here two middle
locations. - Then, we take the average of both values located at the
middle.

$$\huge average\left(\frac{n}{2}, \frac{n}{2}+{1}\right) observations$$
 - n = Number of observations

Example: Find the median of the set {5, 1, 3, 7, 9, 11}.

1.  Arrange the numbers in order: {1, 3, 5, 7, 9, 11}.
2.  Identify the middle number: Total number of observation is 6. Hence,
    6/2 & (6/2) + 1 location. Here, it average of values located at 3rd
    and 4th number.
3.  Third value is 5 and fourth is 7. So, (5+7)/2 = 6
4.  Hence, 6 is the median value. Therefore, the median of the set {5,
    1, 3, 7, 9, 11} is 6.

**Hands-On in R**

Suppose we have a vector of numbers representing the ages of a group of
individuals:

    ages <- c(25, 30, 35, 40, 45, 50, 55)

To calculate the median of these ages in R, you can use the `median()`
function as follows:

-Syntax: `median(x, na.rm = FALSE)`

na.rm is used to remove the missing values from the input vector.

    median_age <- median(ages)
    print(median_age)

    ## [1] 40

Therefore, the median age of this group of individuals is 40.

### Mode

-   The mode is the value that occurs most frequently in a dataset.
-   It is a good measure of central tendency for datasets with a single
    peak or mode.
-   However, it is not always meaningful for datasets with multiple
    modes or no clear mode.

Example: Find the mode of the set {5, 1, 3, 5, 9}.

1.  Identify the most frequent number.
2.  Here, 5 is present twice in the given set. Hence, mode is 5

**Hands-On in R**

Suppose we have a vector of numbers representing the test scores of a
group of students:

    test_scores <- c(85, 72, 90, 68, 93, 80, 77, 88, 85)

    score_table <- table(test_scores)
    mode <- as.numeric(names(score_table)[score_table == max(score_table)])
    print(mode)

    ## [1] 85

Let’s break down this code:

1- table(test\_scores) generates a frequency table for the test\_scores
vector, which counts the occurrences of each unique value.

2- max(score\_table) finds the maximum frequency in the table.

3- names(score\_table)\[score\_table == max(score\_table)\] extracts the
value(s) with the maximum frequency from the frequency table.

4- as.numeric(…) converts the result to a numeric value.

The variable mode will store the mode(s) of the test scores. Note that
there can be multiple modes if multiple values have the same highest
frequency.

## Measures of Dispersion

Measures of dispersion, also known as measures of variability or
measures of spread, are statistical measures that provide information
about the spread or distribution of a dataset. They quantify how much
individual data points deviate from the central tendency of the dataset,
such as the mean or median.

![Figure 4.1: Measures of variability in five data sets having same
mean](Chapter-4-Numerical-Measures_files/figure-markdown_strict/unnamed-chunk-7-1.png)

### Range

The range refers to the difference between the maximum and minimum
values in a dataset. It provides a simple measure of the spread or
variability of the data. To calculate the range, you subtract the
minimum value from the maximum value.

$$\huge Range = Maximum - Minimum$$

Here’s an example to illustrate the concept of range:

Let’s say you have a dataset representing the scores of 10 students on a
mathematics test:

82, 78, 90, 65, 72, 88, 92, 76, 80, 85

To find the range, you first identify the maximum and minimum values in
the dataset. In this case, the maximum value is 92 and the minimum value
is 65.

Range = Maximum value - Minimum value = 92 - 65 = 27

**Hands-On in R**

    # Example dataset
    scores <- c(82, 78, 90, 65, 72, 88, 92, 76, 80, 85)

    # Calculate the range
    range_scores <- range(scores)

    # Print the range
    range_scores

    ## [1] 65 92

The output indicates that the minimum value is 65 and the maximum value
is 92. To calculate the range, you can subtract the minimum value from
the maximum value:

    range <- range_scores[2] - range_scores[1]
    range

    ## [1] 27

So, the range of the scores in this dataset is 27, just as calculated
earlier.

Before moving to interquartile range, it is important to understand
**quartile**.

### Quartile

Quartiles are statistical measures that divide a dataset into four equal
parts. These parts are known as quartiles. The quartiles provide
information about the distribution and spread of the data, particularly
in terms of how it is divided into lower and upper halves.

There are three quartiles: the first quartile (Q1), the second quartile
(Q2), and the third quartile (Q3). The second quartile, Q2, is also
known as the median and divides the dataset into two equal halves.

To calculate the quartiles, you typically arrange the dataset in
ascending order and identify the values that divide it into four equal
parts. The formula to calculate the position of each quartile is:

$$\huge Q1 = \frac{n + 1}{4}$$

$$\huge Q2 = 2 \* \frac{n + 1}{4}$$

$$\huge Q3 = 3 \* \frac{n + 1}{4}$$

where n is the total number of observations in the dataset.

### Interquartile Range

The interquartile range (IQR) is a statistical measure used to describe
the spread or variability of a dataset. It specifically focuses on the
middle 50% of the data and is calculated as the difference between the
third quartile (Q3) and the first quartile (Q1).

Here’s an example to illustrate how to calculate the interquartile
range:

Let’s consider a dataset representing the scores of 12 students on a
physics exam:

76, 80, 72, 85, 90, 65, 88, 82, 78, 70, 92, 76

To calculate the interquartile range, you need to find the first
quartile (Q1) and the third quartile (Q3) of the dataset. The first
quartile represents the 25th percentile, and the third quartile
represents the 75th percentile.

Hands-On in R:

    # Example dataset
    scores <- c(76, 80, 72, 85, 90, 65, 88, 82, 78, 70, 92, 76)

    # Calculate the interquartile range
    iqr_scores <- IQR(scores, type = 2)

    # Print the interquartile range
    iqr_scores

    ## [1] 12.5

In this example, the interquartile range is 12.5. This means that the
middle 50% of the scores in the dataset is spread over a range of 12.5.
The interquartile range is useful in describing the spread of data,
especially when the dataset contains outliers or is not symmetrically
distributed.

### Variance

Variance is a statistical measure that quantifies the dispersion or
spread of a set of data points around their mean (average). It provides
insight into how much the individual data points deviate from the
average value.

Here are some additional things to keep in mind about variance:

-   Variance is a measure of variability, but it does not take into
    account the shape of the distribution. For example, a bimodal
    distribution (two distinct peaks) with the same variance as a
    unimodal distribution (one peak) will have a different shape.
-   Variance is sensitive to outliers. An outlier is a data point that
    is very different from the rest of the data. Outliers can have a
    large impact on the variance, so it is important to remove them
    before calculating the variance.
-   Variance is a sample statistic, which means that it is only an
    estimate of the population variance. The population variance is the
    variance of all the data in a population, not just a sample.

**Sample variance**

$$\huge s^2 = \frac{1}{n-1} \sum\_{i=1}^{n} (x\_i - \bar{x})^2$$
Where: - *s*<sup>2</sup> represents the sample variance. - *n* is the
number of data points in the sample. - *x*<sub>*i*</sub> denotes each
data point. - *x̄* is the sample mean.

\*\*Population variance
$$\huge \sigma^2 = \frac{1}{N} \sum\_{i=1}^{n} (x\_i - \mu)^2$$
Where: - *σ*<sup>2</sup> represents the population variance. - *n* is
the number of data points in the sample. - *x*<sub>*i*</sub> denotes
each data point. - *μ* is the population mean.
