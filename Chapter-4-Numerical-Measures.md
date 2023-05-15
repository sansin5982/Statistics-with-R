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

$$\HUGE\frac{1}{n}\sum\_\\ xi$$

-   ∑ = Summation (Adding all observations)
-   n = Number of observations
-   xi = Individual observation

Example: Find the mean of the set {5, 1, 3, 7, 9}.

-   Total number of observation is 5. Hence, n is 5
-   Summation of all observation is (5 + 1 + 3 + 7 + 9) = 25
-   Mean = 25/5 = 5

**Hands on in R**

Suppose we have a vector of numbers representing the test scores of a
group of students:

    test_scores <- c(85, 72, 90, 68, 93, 80, 77, 88)

To calculate the mean of these test scores in R, we can use the mean()
function:

    mean_score <- mean(test_scores)
    print(mean_score)

    ## [1] 81.625

Therefore, the mean test score of these students is 81.125.

### Median

-   The median is the middle value in a dataset when the values are
    arranged in order.
-   It is less sensitive to outliers than the mean and is a good measure
    of central tendency for datasets that are skewed or have outliers.
-   The median divides the dataset into two equal parts, with 50% of the
    observations above and 50% below the median.
-   Calculation of median also depends on if the observations are odd or
    even.

**ODD number of observations**: - Arrange the observations from smallest
to largest number. - To calculate median value for odd number of
observation, we have to identify middle location.
$$\huge\frac{n + 1}{2}$$
 - Observation located at middle location is will be considered as
median value.

Example: Find the median of the set {5, 1, 3, 7, 9}.

1.  Arrange the numbers in order: {1, 3, 5, 7, 9}.
2.  Identify the middle number: Total number of observation is 5. Hence,
    (5+1)/2 is 3. It means value located at 3rd observation is median
    value.
3.  Hence, 5 is the median value. Therefore, the median of the set {5,
    1, 3, 7, 9} is 5.

**Even number of observations**: - Arrange the observations from
smallest to largest number. - To calculate median value for even number
of observation, we have to identify middle location, here two. - Then,
we take the average of both values located at middle.

$$\huge\frac{n}{2}, \frac{n}{2}+{1}$$

### Mode

-   The mode is the value that occurs most frequently in a dataset.
-   It is a good measure of central tendency for datasets with a single
    peak or mode. \* However, it is not always meaningful for datasets
    with multiple modes or no clear mode.
