# Chi-squared test

The chi-squared test (χ² test) is a statistical hypothesis test that is
used to determine if there is a significant association between two
categorical variables. The test is used to determine whether the
observed frequencies of the categories in the sample differ
significantly from the expected frequencies based on a theoretical
distribution.

The test works by comparing the observed frequencies to the expected
frequencies that would be obtained if the null hypothesis were true. The
null hypothesis in this case is that there is no association between the
two variables.

The test statistic for the chi-squared test is the sum of the squared
differences between the observed and expected frequencies, divided by
the expected frequencies. The resulting value is compared to a
chi-squared distribution with degrees of freedom equal to the number of
categories minus one.

If the calculated value of the chi-squared test statistic is larger than
the critical value from the chi-squared distribution with the
appropriate degrees of freedom, then the null hypothesis is rejected,
and it can be concluded that there is a significant association between
the two variables. On the other hand, if the calculated value is smaller
than the critical value, then the null hypothesis is not rejected, and
it can be concluded that there is no significant association between the
two variables.

The chi-squared test is commonly used in fields such as biology,
psychology, social sciences, and marketing research, among others, to
analyze and interpret categorical data.

<img src="Chi-Squared_value.png" width="20%" style="display: block; margin: auto;" />

## Application of the Chi-squared test

1- **Test of Independence**: The chi-squared test of independence is
used to determine if there is a significant association between two
categorical variables. To illustrate this, let’s consider an example.

Suppose we are interested in whether there is an association between
gender and favorite ice cream flavor. We survey a group of 100 people
and ask them to choose their favorite ice cream flavor from vanilla,
chocolate, and strawberry, and also ask for their gender. The data we
collect is shown in the table below:

<table>
<thead>
<tr class="header">
<th></th>
<th>Vanilla</th>
<th>Chocolate</th>
<th>Strawberry</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Male</td>
<td>20</td>
<td>30</td>
<td>10</td>
<td>60</td>
</tr>
<tr class="even">
<td>Female</td>
<td>25</td>
<td>10</td>
<td>5</td>
<td>40</td>
</tr>
<tr class="odd">
<td>Total</td>
<td>45</td>
<td>40</td>
<td>15</td>
<td>100</td>
</tr>
</tbody>
</table>

We want to determine whether there is an association between gender and
favorite ice cream flavor. To do this, we can perform a chi-squared test
of independence. The null hypothesis is that there is no association
between the two variables, while the alternative hypothesis is that
there is an association.

The first step is to calculate the expected frequencies for each cell
under the assumption that the null hypothesis is true. To do this, we
can use the formula:

Expected frequency = (row total \* column total) / grand total

For example, the expected frequency for the first cell (male-vanilla)
is:

Expected frequency = (60 \* 45) / 100 = 27

We can calculate the expected frequencies for all the cells and fill in
the table below:

<table>
<thead>
<tr class="header">
<th></th>
<th>Vanilla</th>
<th>Chocolate</th>
<th>Strawberry</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Male</td>
<td>27</td>
<td>24</td>
<td>9</td>
<td>60</td>
</tr>
<tr class="even">
<td>Female</td>
<td>18</td>
<td>16</td>
<td>6</td>
<td>40</td>
</tr>
<tr class="odd">
<td>Total</td>
<td>45</td>
<td>40</td>
<td>15</td>
<td>100</td>
</tr>
</tbody>
</table>

Next, we can calculate the chi-squared statistic using the formula:

Chi-squared = sum((observed frequency - expected frequency)^2 / expected
frequency)

We can calculate the contribution to the chi-squared statistic for each
cell using the formula in the parentheses, then sum these contributions
to get the total chi-squared statistic. We can fill in the table below
with the calculations:

<table>
<thead>
<tr class="header">
<th></th>
<th>Vanilla</th>
<th>Chocolate</th>
<th>Strawberry</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Male</td>
<td>1.11</td>
<td>2.31</td>
<td>0.74</td>
<td></td>
</tr>
<tr class="even">
<td>Female</td>
<td>1.08</td>
<td>2.24</td>
<td>0.72</td>
<td></td>
</tr>
<tr class="odd">
<td>Total</td>
<td></td>
<td></td>
<td></td>
<td>7.19</td>
</tr>
</tbody>
</table>

To find the total chi-squared statistic, we sum the values in the Total
row:

Chi-squared = 1.11 + 2.31 + 0.74 + 1.08 + 2.24 + 0.72 = 7.19

Finally, we can compare the chi-squared statistic to a chi-squared
distribution with (r - 1) \* (c - 1) degrees of freedom, where r is the
number of rows and c is the number of columns. In this case, we have
(2 - 1) \* (3 - 1) = 2 degrees of freedom. Using a chi-squared
distribution table or a calculator, we can find the critical value of
chi-squared with 2 degrees of freedom and a significance level of 0.05
to be 5.99.

Since our calculated chi-squared value (7.19) is greater than the 5.99.
Hence, there is an association between gender and favorite ice cream
flavor.

2- **Goodness of fit test**: The chi-squared goodness of fit test, also
known as distribution test, is a hypothesis test that is used to
determine if a set of observed data follows a theoretical distribution.
To illustrate this, let’s consider an example.

Suppose a candy company claims that their bags of candy contain an equal
number of red, blue, green, and yellow candies. To test this claim, we
randomly select a bag of candy and count the number of each color of
candy in the bag. The data we collect is shown in the table below:

<table>
<thead>
<tr class="header">
<th>Color</th>
<th>Red</th>
<th>Blue</th>
<th>Green</th>
<th>Yellow</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Count</td>
<td>8</td>
<td>6</td>
<td>7</td>
<td>9</td>
</tr>
</tbody>
</table>

We want to test whether this observed distribution of colors in the
candy bag is consistent with the candy company’s claim that the bags
contain an equal number of each color. To do this, we can perform a
chi-squared goodness of fit test. The null hypothesis is that the
observed distribution is consistent with the expected distribution,
while the alternative hypothesis is that the observed distribution is
not consistent with the expected distribution.

The first step is to calculate the expected frequencies for each
category under the assumption that the null hypothesis is true. To do
this, we can use the formula:

Expected frequency = (total number of observations \* probability of the
category)

Since there are four categories and the company claims an equal number
of each, the probability of each category is 1/4. The total number of
observations is the sum of the counts, which is 30. Using this
information, we can calculate the expected frequency for each category:

Expected frequency = (30 \* 1/4) = 7.5

We can calculate the expected frequencies for all the categories and
fill in the table below:

<table>
<thead>
<tr class="header">
<th>Color</th>
<th>Red</th>
<th>Blue</th>
<th>Green</th>
<th>Yellow</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Count</td>
<td>8</td>
<td>6</td>
<td>7</td>
<td>9</td>
</tr>
<tr class="even">
<td>Expected</td>
<td>7.5</td>
<td>7.5</td>
<td>7.5</td>
<td>7.5</td>
</tr>
</tbody>
</table>

Next, we can calculate the chi-squared statistic using the formula:

Chi-squared = sum((observed frequency - expected frequency)^2 / expected
frequency)

We can calculate the contribution to the chi-squared statistic for each
category using the formula in the parentheses, then sum these
contributions to get the total chi-squared statistic. We can fill in the
table below with the calculations:

<table>
<thead>
<tr class="header">
<th>Color</th>
<th>Red</th>
<th>Blue</th>
<th>Green</th>
<th>Yellow</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Count</td>
<td>8</td>
<td>6</td>
<td>7</td>
<td>9</td>
</tr>
<tr class="even">
<td>Expected</td>
<td>7.5</td>
<td>7.5</td>
<td>7.5</td>
<td>7.5</td>
</tr>
<tr class="odd">
<td>(O-E)^2/E</td>
<td>0.18</td>
<td>0.11</td>
<td>0.02</td>
<td>0.51</td>
</tr>
</tbody>
</table>

To find the total chi-squared statistic, we sum the values in the last
row:

Chi-squared = 0.18 + 0.11 + 0.02 + 0.51 = 0.82

Finally, we can compare the chi-squared statistic to a chi-squared
distribution with k - 1 degrees of freedom, where k is the number of
categories. In this case, we have k = 4 categories, so we have 3 degrees
of freedom. Using a chi-squared distribution table or a calculator, we
can find the critical value of chi-squared with 3 degrees of freedom and
a significance level of 0.05 to be 7.815.

Since our calculated chi-squared value (0.82) is less than the critical
value (7.815), it means p value is &gt; 0.05, hence null hypothesis is
true.

3- **Homogeneity test**: The chi-squared test for homogeneity is used to
determine if two or more populations have the same distribution of a
categorical variable. To illustrate this, let’s consider an example.

Suppose we want to determine if there is a difference in the preferred
type of fruit between two different regions. We randomly sample
individuals from each region and ask them which type of fruit they
prefer: apples, bananas, or oranges. The data we collect is shown in the
table below:

<table>
<thead>
<tr class="header">
<th></th>
<th>Apples</th>
<th>Bananas</th>
<th>Oranges</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Region 1</td>
<td>60</td>
<td>30</td>
<td>10</td>
</tr>
<tr class="even">
<td>Region 2</td>
<td>40</td>
<td>50</td>
<td>10</td>
</tr>
</tbody>
</table>

We want to test whether the distribution of preferred fruit is the same
in both regions. To do this, we can perform a chi-squared test for
homogeneity. The null hypothesis is that the distribution of preferred
fruit is the same in both regions, while the alternative hypothesis is
that the distribution of preferred fruit is different in at least one
region.

The first step is to calculate the expected frequencies for each
category under the assumption that the null hypothesis is true. To do
this, we can use the formula:

Expected frequency = (total number of observations \* proportion of the
category in both regions)

The total number of observations is the sum of the counts in both
regions, which is 200. We can calculate the proportion of each category
in both regions by adding the counts in both regions and dividing by the
total number of observations. Using this information, we can calculate
the expected frequency for each category in each region:

<table>
<thead>
<tr class="header">
<th></th>
<th>Apples</th>
<th>Bananas</th>
<th>Oranges</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Region 1</td>
<td>60</td>
<td>30</td>
<td>10</td>
</tr>
<tr class="even">
<td>Region 2</td>
<td>40</td>
<td>50</td>
<td>10</td>
</tr>
<tr class="odd">
<td>Total</td>
<td>100</td>
<td>80</td>
<td>20</td>
</tr>
</tbody>
</table>

Next, we can calculate the chi-squared statistic using the formula:

Chi-squared = sum((observed frequency - expected frequency)^2 / expected
frequency)

We can calculate the contribution to the chi-squared statistic for each
category in each region using the formula in the parentheses, then sum
these contributions to get the total chi-squared statistic. We can fill
in the table below with the calculations:

<table>
<thead>
<tr class="header">
<th></th>
<th>Apples</th>
<th>Bananas</th>
<th>Oranges</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Region 1</td>
<td>(60-50)^2/50</td>
<td>(30-40)^2/40</td>
<td>(10-10)^2/10</td>
</tr>
<tr class="even">
<td>Region 2</td>
<td>(40-50)^2/50</td>
<td>(50-40)^2/40</td>
<td>(10-10)^2/10</td>
</tr>
<tr class="odd">
<td>Total</td>
<td>2.4</td>
<td>2.5</td>
<td>0</td>
</tr>
</tbody>
</table>

To find the total chi-squared statistic, we sum the values in the last
row:

Chi-squared = 2.4 + 2.5 + 0 = 4.9

Finally, we can compare the chi-squared statistic to a chi-squared
distribution with (r - 1) x (c - 1) degrees of freedom, where r is the
number of rows and c is the number of columns in the table. In this
case, we have r = 2 rows and c = 3 columns, so we have (2-1) x (3-1) = 2
degrees of freedom. Using a chi-squared distribution table or a
calculator, we can find the critical value of chi-squared with 2 degrees
of freedom. Since our calculated chi-squared statistic of 4.9 is less
than the critical value of 5.99, we fail to reject the null hypothesis
that the distribution of preferred fruit is the same in both regions.
Therefore, we can conclude that there is no significant difference in
the preferred type of fruit between the two regions.

## Application in R

    # Entering the data into vectors
    men = c(150, 120, 45)
    women = c(320, 270, 100)

    # combining the row vectors in matrices, then converting the matrix into a data frame
    food.survey = as.data.frame(rbind(men, women))

    # assigning column names to this data frame
    names(food.survey) = c('Chicken', 'Salad', 'Cake')

    food.survey

    ##       Chicken Salad Cake
    ## men       150   120   45
    ## women     320   270  100

    chisq.test(food.survey)

    ## 
    ##  Pearson's Chi-squared test
    ## 
    ## data:  food.survey
    ## X-squared = 0.13751, df = 2, p-value = 0.9336

    #frequencies
    library(MASS)   
    levels(survey$Smoke) 

    ## [1] "Heavy" "Never" "Occas" "Regul"

    sfreq = table(survey$Smoke) 
    sfreq

    ## 
    ## Heavy Never Occas Regul 
    ##    11   189    19    17

    library(gmodels)

    #2 way cross-tabulation- multivariate frequency table
    #
    #frequencies and relative frequencies
    head(mtcars)

    ##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1

    table(mtcars$carb, mtcars$cyl) 

    ##    
    ##     4 6 8
    ##   1 5 2 0
    ##   2 6 0 4
    ##   3 0 0 3
    ##   4 0 4 6
    ##   6 0 1 0
    ##   8 0 0 1

    CrossTable(mtcars$carb, mtcars$cyl, prop.t=TRUE, prop.r=TRUE, prop.c=TRUE)

    ## 
    ##  
    ##    Cell Contents
    ## |-------------------------|
    ## |                       N |
    ## | Chi-square contribution |
    ## |           N / Row Total |
    ## |           N / Col Total |
    ## |         N / Table Total |
    ## |-------------------------|
    ## 
    ##  
    ## Total Observations in Table:  32 
    ## 
    ##  
    ##              | mtcars$cyl 
    ##  mtcars$carb |         4 |         6 |         8 | Row Total | 
    ## -------------|-----------|-----------|-----------|-----------|
    ##            1 |         5 |         2 |         0 |         7 | 
    ##              |     2.796 |     0.143 |     3.062 |           | 
    ##              |     0.714 |     0.286 |     0.000 |     0.219 | 
    ##              |     0.455 |     0.286 |     0.000 |           | 
    ##              |     0.156 |     0.062 |     0.000 |           | 
    ## -------------|-----------|-----------|-----------|-----------|
    ##            2 |         6 |         0 |         4 |        10 | 
    ##              |     1.910 |     2.188 |     0.032 |           | 
    ##              |     0.600 |     0.000 |     0.400 |     0.312 | 
    ##              |     0.545 |     0.000 |     0.286 |           | 
    ##              |     0.188 |     0.000 |     0.125 |           | 
    ## -------------|-----------|-----------|-----------|-----------|
    ##            3 |         0 |         0 |         3 |         3 | 
    ##              |     1.031 |     0.656 |     2.170 |           | 
    ##              |     0.000 |     0.000 |     1.000 |     0.094 | 
    ##              |     0.000 |     0.000 |     0.214 |           | 
    ##              |     0.000 |     0.000 |     0.094 |           | 
    ## -------------|-----------|-----------|-----------|-----------|
    ##            4 |         0 |         4 |         6 |        10 | 
    ##              |     3.438 |     1.502 |     0.604 |           | 
    ##              |     0.000 |     0.400 |     0.600 |     0.312 | 
    ##              |     0.000 |     0.571 |     0.429 |           | 
    ##              |     0.000 |     0.125 |     0.188 |           | 
    ## -------------|-----------|-----------|-----------|-----------|
    ##            6 |         0 |         1 |         0 |         1 | 
    ##              |     0.344 |     2.790 |     0.438 |           | 
    ##              |     0.000 |     1.000 |     0.000 |     0.031 | 
    ##              |     0.000 |     0.143 |     0.000 |           | 
    ##              |     0.000 |     0.031 |     0.000 |           | 
    ## -------------|-----------|-----------|-----------|-----------|
    ##            8 |         0 |         0 |         1 |         1 | 
    ##              |     0.344 |     0.219 |     0.723 |           | 
    ##              |     0.000 |     0.000 |     1.000 |     0.031 | 
    ##              |     0.000 |     0.000 |     0.071 |           | 
    ##              |     0.000 |     0.000 |     0.031 |           | 
    ## -------------|-----------|-----------|-----------|-----------|
    ## Column Total |        11 |         7 |        14 |        32 | 
    ##              |     0.344 |     0.219 |     0.438 |           | 
    ## -------------|-----------|-----------|-----------|-----------|
    ## 
    ## 

# Reference:

<https://datatab.net/tutorial/chi-square-test> More reference to be
added.
