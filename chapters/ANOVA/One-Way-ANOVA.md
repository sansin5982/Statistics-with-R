<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# One-Way ANOVA

**One-Way Analysis of Variance (ANOVA)** is a statistical method used
**to compare the means of three or more independent groups** to
determine if at least one group mean is significantly different from the
others.

-   To **test whether the means of three or more independent groups are
    significantly different**.
-   Helps determine whether **variation among groups is greater than
    variation within groups**.

#### Why Do We Use One-Way ANOVA?

-   **T-test limitation**: A **t-test** can only compare two groups. If
    we compare multiple groups using t-tests, it increases the risk of
    **Type I error** (false positives).
-   **ANOVA handles multiple groups simultaneously** while maintaining
    statistical integrity.

## Assumptions of One-Way ANOVA

### 1. Independence:

-   Observations must be independent within and across groups.

### 2. Normality:

-   The dependent variable should be **normally distributed** in each
    group.

### 3. Homogeneity of Variance (Homoskedasticity):

-   Variances should be **equal** across groups (can be tested using
    Levene’s Test).

## One-Way ANOVA Formula

### Total Variance

ANOVA splits the total variation in data into two components:

#### 1. Between-group variance (explained variance)

#### 2. Within-group variance (unexplained variance)

$$
\large Total Varaince = Between-Group \\Variance \\+ \\Within-Group  \\Variance
$$

#### Key Formulas

#### 1. Total Sum of Squares (SST)

$$
\Large SST = \underset{i=1}{\sum}^{k} \underset{j=1}{\sum}^{ni} \\(X{ij} \\- \bar{X}{total} )^2
$$

Where:

-   *k* = number of groups
-   *n**i* = number of observations in group
-   *X**i**j* = observation in group *i*, *j*
-   *X̄**t**o**t**a**l* = overall mean

#### 2. Between-Group Sum of Squares (SSB)

$$
\Large SSB = \underset{i=1}{\sum}^{k} \\n{i}  \\(\bar X{i} \\- \bar{X}{total} )^2
$$

-   *X̄**i* = mean of group *i*

#### 3. Within-Gorup Sum of Squares (SSW)

$$
\Large SSW = \underset{i=1}{\sum}^{k} \underset{j=1}{\sum}^{ni} \\(X{ij} \\- \bar{X}{i} )^2
$$

#### 4. Degrees of Freedom

-   df between groups = *k* − 1
-   df within groups = *N* − *k*
-   df total = *n* − 1
    -   Where n is the total number of observations

#### 5. Mean Square Between

$$
\Large MSB = \frac{SSB}{df {\scriptstyle between}}
$$

#### 5. Mean Square Between

$$
\Large MSB = \frac{SSB}{df {\scriptstyle between}}
$$

#### 6. Mean Square Within

$$
\Large MSW = \frac{SSW}{df {\scriptstyle within}}
$$

#### 7. F-statistics

$$
\Large F = \frac{MSB}{MSW}
$$

-   If *F* **is significantly large**, we reject the null hypothesis
    *H*0 and conclude that **at least one group mean is different**.

#### 8. Post-Hoc Analysis

After finding a significant **F-statistic** in One-Way ANOVA, we need to
determine **which specific groups differ** from each other. This is done
using **post-hoc tests** (multiple comparison tests). \* ANOVA tells us
only that at least one group is different, but it does not tell us which
groups are different. \* Multiple Comparisons Problem: If we perform
multiple t-tests between each pair, the risk of Type I error increases.
\* Post-hoc tests adjust for multiple comparisons to maintain
statistical integrity.

#### Common Post-Hoc tests

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Test</th>
<th style="text-align: left;">Purpose</th>
<th style="text-align: left;">Assumption</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><strong>Tukey’s HSD (Honest Significant
Difference)</strong></td>
<td style="text-align: left;">Compares all pairs, controls type 1
error</td>
<td style="text-align: left;">Assumes equal variance</td>
</tr>
<tr class="even">
<td style="text-align: left;"><strong>Bonferrono
correction</strong></td>
<td style="text-align: left;">Adjusts significance level to reduce type
1 error</td>
<td style="text-align: left;">Conservative method</td>
</tr>
<tr class="odd">
<td style="text-align: left;"><strong>Scheffe’s test</strong></td>
<td style="text-align: left;">Suitable for unequal sample sizes</td>
<td style="text-align: left;">Robust</td>
</tr>
<tr class="even">
<td style="text-align: left;"><strong>Dunnett’s test</strong></td>
<td style="text-align: left;">Compares each group to a control
group</td>
<td style="text-align: left;">Controls type 1 error</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Games-Howell Test</td>
<td style="text-align: left;">Used when variances are unequal</td>
<td style="text-align: left;">Does not assume equal variance</td>
</tr>
</tbody>
</table>

#### 9. Example

A researcher wants to test whether three different diets (A, B, C)
result in different weight loss. The weight loss (in kg) after 6 weeks
is recorded for each diet:

<table>
<thead>
<tr class="header">
<th style="text-align: left;">Diet</th>
<th style="text-align: left;">Weight loss</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">A</td>
<td style="text-align: left;">2</td>
</tr>
<tr class="even">
<td style="text-align: left;">A</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="odd">
<td style="text-align: left;">A</td>
<td style="text-align: left;">5</td>
</tr>
<tr class="even">
<td style="text-align: left;">A</td>
<td style="text-align: left;">1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">A</td>
<td style="text-align: left;">4</td>
</tr>
<tr class="even">
<td style="text-align: left;">B</td>
<td style="text-align: left;">3</td>
</tr>
<tr class="odd">
<td style="text-align: left;">B</td>
<td style="text-align: left;">5</td>
</tr>
<tr class="even">
<td style="text-align: left;">B</td>
<td style="text-align: left;">4</td>
</tr>
<tr class="odd">
<td style="text-align: left;">B</td>
<td style="text-align: left;">6</td>
</tr>
<tr class="even">
<td style="text-align: left;">B</td>
<td style="text-align: left;">5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">C</td>
<td style="text-align: left;">6</td>
</tr>
<tr class="even">
<td style="text-align: left;">C</td>
<td style="text-align: left;">7</td>
</tr>
<tr class="odd">
<td style="text-align: left;">C</td>
<td style="text-align: left;">8</td>
</tr>
<tr class="even">
<td style="text-align: left;">C</td>
<td style="text-align: left;">5</td>
</tr>
<tr class="odd">
<td style="text-align: left;">C</td>
<td style="text-align: left;">7</td>
</tr>
</tbody>
</table>

#### Step 1: Calculate Group means

$$
\large \bar{X{\scriptstyle A}} = \frac{2+3+5+1+4} {5} = 3
$$

$$
\large \bar{X{\scriptstyle B}} = \frac{3+5+4+6+5} {5} = 4.6
$$

$$
\large \bar{X{\scriptstyle C}} = \frac{6+7+8+5+7} {5} = 6.6
$$

#### Step 2: Calculate Overall Mean

$$
\large \bar{X{\scriptstyle Total}} = \frac{(2+3+5+1+4)+(3+5+4+6+5)+(6+7+8+5+7)} {15} = 4.73
$$

#### Step 3: Compute SST, SSB, SSW

$$
SSB = \underset{i=1}{\sum}^{k} \\n{i}  \\(\bar X{\scriptstyle i} \\- \bar{X}{\scriptstyle total} )^2
$$

#### For group A:

$$
\large SSB = 5(3 - 4.73)^2 = 14.95
$$
\#### For group B:

$$
\large SSB = 5(4.6 - 4.73)^2 = 0.10
$$

#### For group C:

$$
\large SSB = 5(6.6 - 4.73)^2 = 17.50
$$

#### TOTAL SSB:

$$
\large SSB = 14.95 + 0.10 + 17.50 = 30.93
$$
