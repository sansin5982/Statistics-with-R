<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Sampling Distribution of Mean

## Statistical Inference

## Sampling Distribution?

A **sampling distribution** is the probability distribution of a given
statistic (like the mean) based on a \*\*random sample\*.

> In simpler terms: Imagine we repeatedly take samples from a population
> and compute the sample mean each time. The distribution of all those
> sample means is called the **sampling distribution of the mean**.

#### Example:

Suppose a population has 10,000 students with an average height of 160
cm. If we randomly **select samples of 50 students** and calculate their
mean height every time, you get many different means. The **distribution
of those sample means** is the **sampling distribution of the mean**.

-   It helps us **estimate population parameters** using sample
    statistics.
-   Forms the basis of **confidence intervals** and **hypothesis
    testing**.

### Characteristics of the Sampling Distribution of the Mean

Assume:

-   Population mean = μ
-   Population standard deviation = σ
-   Sample size = n

Then:

<table>
<colgroup>
<col style="width: 37%" />
<col style="width: 62%" />
</colgroup>
<thead>
<tr>
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Mean of sampling distribution</strong></td>
<td>Equal to population mean: <strong>E(X̄) = μ</strong></td>
</tr>
<tr>
<td><strong>Standard deviation</strong></td>
<td>Called the <strong>Standard Error (SE)</strong>: <strong>SE = σ /
√n</strong></td>
</tr>
<tr>
<td><strong>Shape</strong></td>
<td>Approaches normal as n increases (Central Limit Theorem)</td>
</tr>
</tbody>
</table>

## Standard Error (SE)?

The **Standard Error** is the **standard deviation of the sampling
distribution of the mean**.

Formula:

$$
\large SE = \frac {\sigma}{\sqrt n}
$$

#### Importance:

-   Smaller SE → more precise estimate of the population mean.
-   As **sample size increases**, SE **decreases** (more reliable
    estimate).

## Central Limit Theorem (CLT)

The **Central Limit Theorem** states that:

> Regardless of the population’s distribution, the sampling distribution
> of the mean **approaches a normal distribution** as the sample size
> becomes large (typically **n ≥ 30**).

-   **Population**: Could be skewed, uniform, etc.
-   **Sample means**: As we take more and more samples, their
    distribution starts to look like a bell curve.

#### Key Points

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 81%" />
</colgroup>
<thead>
<tr>
<th>Term</th>
<th>Explanation</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>n ≥ 30</strong></td>
<td>Sample size is large enough → CLT applies</td>
</tr>
<tr>
<td><strong>μ</strong></td>
<td>Mean of sampling distribution = Mean of population</td>
</tr>
<tr>
<td><strong>SE = σ/√n</strong></td>
<td>Standard deviation of the sampling distribution</td>
</tr>
<tr>
<td><strong>Shape</strong></td>
<td>Becomes normal even if original population is not normal</td>
</tr>
</tbody>
</table>

### Applications of CLT:

-   Construction of **confidence intervals**
-   **Hypothesis testing** (Z-tests, t-tests)
-   Simplifies complex population distributions

### Applications of Sampling Distribution of Mean

<table>
<colgroup>
<col style="width: 26%" />
<col style="width: 73%" />
</colgroup>
<thead>
<tr>
<th>Use Case</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Confidence Intervals</strong></td>
<td>Estimate population mean using sample mean ± margin of error</td>
</tr>
<tr>
<td><strong>Hypothesis Testing</strong></td>
<td>Test claims about the population mean using sampling
distribution</td>
</tr>
<tr>
<td><strong>Quality Control</strong></td>
<td>Identify whether production means vary significantly from
standard</td>
</tr>
<tr>
<td><strong>Polling &amp; Surveys</strong></td>
<td>Generalize results from samples to entire population</td>
</tr>
</tbody>
</table>

## Real-Life Example:

#### Scenario:

A coffee company wants to ensure that the **average caffeine content**
in its drinks is 95mg.

### Steps:

1.  They take **samples of 40 bottles** from each batch.

2.  Calculate the **sample mean caffeine**.

3.  Repeat this process for **many batches**.

4.  The distribution of those means is the **sampling distribution**.

#### Why?

Helps determine if any batch **deviates significantly** from the target.

They apply the **CLT** to assume normality and perform **Z-tests** for
quality control.
