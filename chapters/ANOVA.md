<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Analysis of Variance (ANOVA)

**Analysis of Variance (ANOVA)** is a **statistical method used to
compare the means of three or more groups** to determine if at least one
of the group means is significantly different from the others. It
extends the t-test, which is limited to comparing only **two groups**.

The ANOVA test is based on **F-distribution** and is used when:

-   There are three or more independent groups.
-   The dependent variable is continuous (e.g., height, weight, test
    scores).
-   The independent variable is categorical (e.g., different treatments,
    different education levels).

## History of ANOVA

-   **Developed by Ronald A. Fisher** in the 1920s as a method to
    analyze agricultural experiments.
-   Fisher introduced the **F-test**, which is used in ANOVA to test if
    group variances are significantly different.
-   Over time, ANOVA became a key method in medical research,
    psychology, economics, and genetics.

### F-Distribution:

The **F-distribution** is a probability distribution used mainly in
**ANOVA** and **regression analysis**. It helps us compare **variability
between multiple groups** and determine if the differences between them
are statistically significant.

Imagine we are a teacher, and we have three different classes of
students. You want to check:

-   Are the average scores of these classes significantly different?
-   Or are the differences just due to random variation?

To do this, you compare: 1. **Between-Group Variance (Difference Between
Classes)**: How much do the class averages differ from each other? 2.
**Within-Group Variance (Difference Within Each Class)**: How much do
individual students in the same class differ from each other?

The F-statistic is the ratio of these two:

$$
\large F = \frac{(Between \\Group \\Variance)}{(Within \\Group  \\Variance)}
$$
\* If F is large → The groups are likely different. \* If F is small →
The groups are likely similar.

![](ANOVA_files/figure-markdown_strict/unnamed-chunk-1-1.png)

[⬅ Back to Home](../index.md)
