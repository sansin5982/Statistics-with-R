<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Chi-Squared Test

## Introduction

The chi-squared test (χ² test) is a statistical hypothesis test **used
to determine if there is a significant association between two
categorical variables**. The test determines whether the observed
frequencies of the categories in the sample differ significantly from
the expected frequencies based on a theoretical distribution.

If the **calculated value of the chi-squared test statistic is larger
than the critical value** from the chi-squared distribution with the
appropriate degrees of freedom, then the **null hypothesis is
rejected**, and it can be concluded that there is a significant
association between the two variables. On the other hand, if the
calculated value is smaller than the critical value, then the null
hypothesis is not rejected, and it can be concluded that there is no
significant association between the two variables.

Chi-squared tests are widely applied in biological research, such as in
genetics to examine allele distributions or in epidemiology to assess
disease prevalence across different groups.

$$
\large \chi^2 = \sum \frac{(O{\scriptstyle ij} - E{\scriptstyle ij})^2}{E{\scriptstyle ij}}
$$

where:  
\* *O*\_*i**j* = observed frequency  
\* *E*\_*i**j* = expected frequency

## Types of Chi-squared Tests

### 1. **Test of Independence**

The chi-squared test of independence examines whether two categorical
variables are associated.

#### **Example: Association Between Blood Type and Disease Susceptibility**

Suppose a study investigates whether blood type is associated with
susceptibility to a specific disease. The observed data is:

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: left;">Disease</th>
<th style="text-align: left;">No Disease</th>
<th style="text-align: left;">Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">A</td>
<td style="text-align: left;">30</td>
<td style="text-align: left;">70</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="even">
<td style="text-align: left;">B</td>
<td style="text-align: left;">25</td>
<td style="text-align: left;">75</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="odd">
<td style="text-align: left;">O</td>
<td style="text-align: left;">45</td>
<td style="text-align: left;">55</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="even">
<td style="text-align: left;">AB</td>
<td style="text-align: left;">20</td>
<td style="text-align: left;">80</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Total</td>
<td style="text-align: left;">120</td>
<td style="text-align: left;">280</td>
<td style="text-align: left;">400</td>
</tr>
</tbody>
</table>

To test the independence of blood type and disease status, we compute
expected frequencies using:

$$
\large E{\scriptstyle ij} = \frac{(row\\total \times column\\total)}{grand\\total} 
$$

-   **Row Totals**:
    -   A: 100

    -   B: 100

    -   O: 100

    -   AB: 100
-   **Column Totals**:
    -   Disease: 120

    -   No Disease: 280
-   **Grand Total**: 400

### Computing Expected Frequency from observed frequency

#### For blood type A:

-   **Disease**

$$
\\E{\scriptstyle A,Disease} = \frac{(100 \times 120)}{400} \\= \frac{12000}{400} = 30
$$

-   **No Disease**

$$
\\E{\scriptstyle A,NoDisease} = \frac{(100 \times 280)}{400} \\= \frac{280000}{400} = 70
$$

#### For blood type B:

-   **Disease**

$$
\\E{\scriptstyle B,Disease} = \frac{(100 \times 120)}{400} \\= \frac{12000}{400} = 30
$$

-   **No Disease**

$$
\\E{\scriptstyle B,NoDisease} = \frac{(100 \times 280)}{400} \\= \frac{280000}{400} = 70
$$

#### For blood type O:

-   **Disease**

$$
\\E{\scriptstyle O,Disease} = \frac{(100 \times 120)}{400} \\= \frac{12000}{400} = 30
$$

-   **No Disease**

$$
\\E{\scriptstyle O,NoDisease} = \frac{(100 \times 280)}{400} \\= \frac{280000}{400} = 70
$$

#### For blood type AB:

-   **Disease**

$$
\\E{\scriptstyle AB,Disease} = \frac{(100 \times 120)}{400} \\= \frac{12000}{400} = 30
$$

-   **No Disease**

$$
\\E{\scriptstyle AB,NoDisease} = \frac{(100 \times 280)}{400} \\= \frac{280000}{400} = 70
$$

#### Expected frequency calculated

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: left;">Disease</th>
<th style="text-align: left;">No Disease</th>
<th style="text-align: left;">Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">A</td>
<td style="text-align: left;">30</td>
<td style="text-align: left;">70</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="even">
<td style="text-align: left;">B</td>
<td style="text-align: left;">30</td>
<td style="text-align: left;">70</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="odd">
<td style="text-align: left;">O</td>
<td style="text-align: left;">30</td>
<td style="text-align: left;">70</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="even">
<td style="text-align: left;">AB</td>
<td style="text-align: left;">30</td>
<td style="text-align: left;">70</td>
<td style="text-align: left;">100</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Total</td>
<td style="text-align: left;">120</td>
<td style="text-align: left;">280</td>
<td style="text-align: left;">400</td>
</tr>
</tbody>
</table>

#### Compute Chi-squared Contributions

We compute:

$$
\large \frac{(O{\scriptstyle ij} - E{\scriptstyle ij})^2}{E{\scriptstyle ij}}
$$

for each cell.

#### **For Blood Type A:**

-   **Disease:**

$$
\frac{(30 - 30.0)^2}{30.0} = \frac{0^2}{30.0} = 0.000
$$

-   **No Disease:**

$$
\frac{(70 - 70.0)^2}{70.0} = \frac{0^2}{70.0} = 0.000
$$

#### **For Blood Type B:**

-   **Disease:**

$$
\frac{(25 - 30.0)^2}{30.0} = \frac{(-5)^2}{30.0} = \frac{25}{30.0} = 0.833
$$

-   **No Disease:**

$$
\frac{(75 - 70.0)^2}{70.0} = \frac{5^2}{70.0} = \frac{25}{70.0} = 0.357
$$

#### **For Blood Type O:**

-   **Disease:**

$$
\frac{(45 - 30.0)^2}{30.0} = \frac{15^2}{30.0} = \frac{225}{30.0} = 7.500
$$

-   **No Disease:**

$$
\frac{(55 - 70.0)^2}{70.0} = \frac{(-15)^2}{70.0} = \frac{225}{70.0} = 3.214
$$

#### **For Blood Type AB:**

-   **Disease:**

$$
\frac{(20 - 30.0)^2}{30.0} = \frac{(-10)^2}{30.0} = \frac{100}{30.0} = 3.333
$$

-   **No Disease:**

$$
\frac{(80 - 70.0)^2}{70.0} = \frac{10^2}{70.0} = \frac{100}{70.0} = 1.429
$$

### Compute the Total Chi-squared Statistic

Summing all contributions:

*χ*<sup>2</sup> = 0.000 + 0.000 + 0.833 + 0.357 + 7.500 + 3.214 + 3.333 + 1.429

*χ*<sup>2</sup> = 16.67
Thus, the final chi-squared value is **16.67**.

### Degrees of Freedom (df) Calculation

The degrees of freedom (df) for a chi-squared test of independence is
calculated using the formula:

*d**f* = (*r* − 1) × (*c* − 1)

where: - *r* = numbers of rows (excluding total), here 4 - *r* = numbers
of columns (excluding total), here 2

Now, calculating df:

*d**f* = (4 − 1) × (2 − 1) = 3 × 1 = 3

#### Judging Significance with the Critical Value

To determine whether the observed association is statistically
significant, we compare our calculated chi-squared value
(*χ*<sup>2</sup> = 16.67) to the **critical chi-squared** value from a
chi-squared distribution table at a given significance level (*α*).

**Step 1: Find the Critical Value**

Using a chi-squared table at df = 3 and *α* = 0.05 (95% confidence
level), the critical value is:

*χ*<sub>*c**r**i**t**i**c**a**l*</sub><sup>2</sup> = 7.815
**Step 2: Compare with Calculated Chi-square**

-   If *χ*<sub>*c**a**l**c**u**l**a**t**e**d*</sub><sup>2</sup> &gt;
    *χ*<sub>*c**r**i**t**i**c**a**l*</sub><sup>2</sup>: **reject the
    null hypothesis**

-   If *χ*<sub>*c**a**l**c**u**l**a**t**e**d*</sub><sup>2</sup> &lt;
    *χ*<sub>*c**r**i**t**i**c**a**l*</sub><sup>2</sup>: **accept the
    null hypothesis**

Our calculated chi-squared value:

*χ*<sup>2</sup> = 16.67 &gt; 7.815
**Conclusion**: We reject the null hypothesis, meaning **there is a
statistically significant association between blood type and disease**
at the 0.05 significance level.

#### **Performing Chi-squared Test in R**

    blood_type <- matrix(c(30, 70, 25, 75, 45, 55, 20, 80), nrow = 4, byrow = TRUE)
    rownames(blood_type) <- c("A", "B", "O", "AB")
    colnames(blood_type) <- c("Disease", "No Disease")
    chisq.test(blood_type)

    ## 
    ##  Pearson's Chi-squared test
    ## 
    ## data:  blood_type
    ## X-squared = 16.667, df = 3, p-value = 0.0008275

Result is same. Hence We reject the null hypothesis, meaning **there is
a statistically significant association between blood type and disease**
at the 0.05 significance level.

### 2. **Goodness of Fit Test**

The chi-squared goodness of fit test assesses whether an observed
categorical distribution matches an expected distribution.

#### **Example: Mendelian Inheritance in Pea Plants**

Mendelian genetics predicts that in a monohybrid cross, offspring should
follow a 3:1 ratio of dominant to recessive phenotypes.

Observed Data:

<table>
<thead>
<tr class="header">
<th>Phenotype</th>
<th>Observed</th>
<th>Expected</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Purple</td>
<td>315</td>
<td>337.5</td>
</tr>
<tr class="even">
<td>White</td>
<td>105</td>
<td>112.5</td>
</tr>
</tbody>
</table>

#### **Performing Goodness of Fit Test in R**

    observed <- c(315, 105)
    expected <- c(337.5, 112.5)
    chisq.test(observed, p = c(0.75, 0.25))

    ## 
    ##  Chi-squared test for given probabilities
    ## 
    ## data:  observed
    ## X-squared = 0, df = 1, p-value = 1

### 3. **Homogeneity Test**

The chi-squared test for homogeneity assesses whether different
populations have the same distribution of a categorical variable.

#### **Example: Genetic Mutation Across Different Populations**

A study examines whether the frequency of a specific genetic mutation
differs across three populations.

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: left;">Mutation Present</th>
<th style="text-align: left;">No Mutation</th>
<th style="text-align: left;">Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Population 1</td>
<td style="text-align: left;">50</td>
<td style="text-align: left;">150</td>
<td style="text-align: left;">200</td>
</tr>
<tr class="even">
<td style="text-align: left;">Population 2</td>
<td style="text-align: left;">60</td>
<td style="text-align: left;">140</td>
<td style="text-align: left;">200</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Population 3</td>
<td style="text-align: left;">40</td>
<td style="text-align: left;">160</td>
<td style="text-align: left;">200</td>
</tr>
<tr class="even">
<td style="text-align: left;">Total</td>
<td style="text-align: left;">150</td>
<td style="text-align: left;">450</td>
<td style="text-align: left;">600</td>
</tr>
</tbody>
</table>

#### **Performing Homogeneity Test in R**

    mutation_data <- matrix(c(50, 150, 60, 140, 40, 160), nrow = 3, byrow = TRUE)
    rownames(mutation_data) <- c("Population 1", "Population 2", "Population 3")
    colnames(mutation_data) <- c("Mutation Present", "No Mutation")
    chisq.test(mutation_data)

    ## 
    ##  Pearson's Chi-squared test
    ## 
    ## data:  mutation_data
    ## X-squared = 5.3333, df = 2, p-value = 0.06948

## Application in R Using In-built Datasets

Using the `survey` dataset from the `MASS` package, we examine smoking
habits.

    library(MASS)
    levels(survey$Smoke)

    ## [1] "Heavy" "Never" "Occas" "Regul"

Creating a frequency table:

    table(survey$Smoke)

    ## 
    ## Heavy Never Occas Regul 
    ##    11   189    19    17

Performing chi-square test:

    chisq.test(table(survey$Smoke))

    ## 
    ##  Chi-squared test for given probabilities
    ## 
    ## data:  table(survey$Smoke)
    ## X-squared = 382.51, df = 3, p-value < 2.2e-16

## Conclusion

The chi-squared test is a powerful tool for analyzing categorical data
in biology, genetics, and epidemiology. Its applications include
evaluating genetic inheritance, disease associations, and population
differences.

## References

1.  Agresti, A. (2018). *An Introduction to Categorical Data Analysis*.
    Wiley.
2.  Sokal, R. R., & Rohlf, F. J. (2012). *Biometry: The Principles and
    Practice of Statistics in Biological Research*. W. H. Freeman.
3.  Zar, J. H. (2010). *Biostatistical Analysis*. Pearson.
