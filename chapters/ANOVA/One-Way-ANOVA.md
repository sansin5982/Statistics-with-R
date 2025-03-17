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
