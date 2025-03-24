<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Independent Sample T-test

The **Independent Two-Sample T-Test** (also known as the unpaired
t-test) is used to determine whether the **means of two independent
groups** are statistically significantly different.

It is commonly applied in cases such as: - Comparing test scores between
two different classes - Comparing the effectiveness of two treatments on
separate patient group

## Hypotheses

### Null Hypothesis (*H*<sub>0</sub>)

$$
\large H{\scriptstyle 0}: \mu{\scriptstyle 1} = \mu{\scriptstyle 2}
$$

### Alternative Hypothesis (*H*<sub>1</sub>)

$$
\large H{\scriptstyle 1}: \mu{\scriptstyle 1} \ne \mu{\scriptstyle 2}
$$

## Formulas

### Equal Variances Assumed (Pooled T-Test)

$$
\Large t = \frac{\bar{X{\scriptstyle 1}} - \bar{X{\scriptstyle 2}}}{s{\scriptstyle p} \sqrt{\frac{1}{n{\scriptstyle 1}} + \frac{1}{n{\scriptstyle 2}}}}
$$

Where:

$$S{\scriptstyle p} = \sqrt{\frac{(n{\scriptstyle 1} - 1)s{\scriptstyle 1^2} + (n{\scriptstyle 2} - 1)s{\scriptstyle 2^2}}{n{\scriptstyle 1} + n{\scriptstyle 2} - 2}}$$

-   is the pooled standard deviation

### Unequal Variances (Welch’s T-Test)

$$
\Large t = \frac{\bar{X{\scriptstyle 1}} - \bar{X{\scriptstyle 2}}}{\sqrt{\frac{s{\scriptstyle 1^2}}{n{\scriptstyle 1}} + \frac{s{\scriptstyle 2^2}}{n{\scriptstyle 2}}}}
$$

#### Degrees of Freedom (Welch–Satterthwaite approximation):

$$
\Large df = \frac{\left(\frac{s{\scriptstyle 1^2}}{n{\scriptstyle 1}} + \frac{s{\scriptstyle 2^2}}{n{\scriptstyle 2}}\right)^2}{\frac{(s{\scriptstyle 1^2}/n{\scriptstyle 1})^2}{n{\scriptstyle 1} - 1} + \frac{(s{\scriptstyle 2^2}/n{\scriptstyle 2})^2}{n{\scriptstyle 2} - 1}}
$$

-   Can be two-tailed (default) or one-tailed.

## Assumptions

-   Both groups are **independent**
-   Data is **normally distributed** within each group
-   Variances are **equal** (for pooled t-test), or Welch’s test used
    when they are not
-   Data is on **interval/ratio** scale

## Example (Unequal Variance Case)

### Scenario:

You want to test whether men and women differ in protein intake.

#### Data:

-   **Men**: 72, 75, 78, 71, 74 →
    *X̄*<sub>1</sub> = 74, *s*<sub>1</sub><sup>2</sup> = 6.5, *n*<sub>1</sub> = 5
-   **Women**: 68, 66, 70, 65, 69 →
    *X̄*<sub>2</sub> = 67.6, *s*<sub>2</sub><sup>2</sup> = 3.3, *n*<sub>2</sub> = 5

### Step-by-step (Welch’s T-Test):

**1. Compute t-statistic**
$$
\large t = \frac{74 - 67.6}{\sqrt{\frac{6.5}{5} + \frac{3.3}{5}}} = \frac{6.4}{\sqrt{1.3 + 0.66}} = \frac{6.4}{1.4} \approx 4.57
$$

**2. Compute degrees of freedom**
$$
\large df = \frac{1.96^2}{\frac{(1.3)^2}{4} + \frac{(0.66)^2}{4}} = \frac{3.84}{0.5314} \approx 7.23 \Rightarrow df \approx 7
$$

**3. Critical value**

$$ \large \alpha = 0.05, two-tailed): t\_{critical} = \pm 2.365$$

**4. Decision**: Since:

$$\large 4.57 &gt; 2.365, reject H\_0$$

-   significant difference
