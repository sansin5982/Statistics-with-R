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
\Large t = \frac{\bar{X{\scriptstyle 1}} - \bar{X{\scriptstyle 2}}}{s{\scriptstyle p} \sqrt{\frac{1}{n\_1} + \frac{1}{n\_2}}}
$$

Where:

-   $s\_p = \sqrt{\frac{(n\_1 - 1)s\_1^2 + (n\_2 - 1)s\_2^2}{n\_1 + n\_2 - 2}}$
    is the pooled standard deviation

### Unequal Variances (Welch’s T-Test)

$$
\Large t = \frac{\bar{X}\_1 - \bar{X}\_2}{\sqrt{\frac{s\_1^2}{n\_1} + \frac{s\_2^2}{n\_2}}}
$$

#### Degrees of Freedom (Welch–Satterthwaite approximation):

$$
\Large df = \frac{\left(\frac{s\_1^2}{n\_1} + \frac{s\_2^2}{n\_2}\right)^2}{\frac{(s\_1^2/n\_1)^2}{n\_1 - 1} + \frac{(s\_2^2/n\_2)^2}{n\_2 - 1}}
$$
 - Can be two-tailed (default) or one-tailed.

## Assumptions

-   Both groups are **independent**
-   Data is **normally distributed** within each group
-   Variances are **equal** (for pooled t-test), or Welch’s test used
    when they are not
-   Data is on **interval/ratio** scale
