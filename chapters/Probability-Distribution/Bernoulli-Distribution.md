<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Bernoulli Distribution

The **Bernoulli Distribution** is one of the **simplest discrete
probability distributions**. It models a random variable where there are
only **two possible outcomes** — typically called “success” and
“failure”.

------------------------------------------------------------------------

#### Real-Life Examples

-   Tossing a coin (Heads = 1, Tails = 0)  
-   Checking if a light bulb is working (Yes = 1, No = 0)  
-   A customer buying a product (Buys = 1, Doesn’t buy = 0)

------------------------------------------------------------------------

### Bernoulli trials

A **Bernoulli trial** is a **single experiment** or action that:

-   Has exactly **two possible outcomes** (usually labeled as
    **“success”** and **“failure”**)

-   The **probability of success is fixed**

-   Each trial is **independent** of the others

#### Explanation

Imagine flipping a coin:

-   We either get **Heads (success)** or **Tails (failure)**

-   Each flip is **independent** of the others

-   Probability of success (e.g., Heads) is constant (0.5)

That’s a **Bernoulli trial**.

------------------------------------------------------------------------

## Definition

A random variable *X* follows a **Bernoulli distribution** if it takes
only two values:

$$
X = 
\begin{cases} 
1 & \text{with probability } p \\
0 & \text{with probability } 1 - p 
\end{cases}
$$

Where:

-   *P*(*X* = 1) = *p* is the **probability of success** (i.e., getting
    a 1)  
-   *P*(*X* = 1) = 1 − *p* is the **probability of failure** (i.e.,
    getting a 0)

------------------------------------------------------------------------

### Properties

#### Mean

The **mean (or expected value)** is the **average outcome we’d** expect
over many repeated trials.

#### Example (Coin Toss):

If you toss a fair coin:

-   Heads = 1 (Success)
-   Tails = 0 (Failure)
-   *p* = 0.5

Then over 100 tosses, we’d expect **about 50 heads**, so the **mean =
0.5**

#### Mean formula for Bernoulli Distribution:

$$
\large \mu = E(X) = p
$$
\#### Variance Variance tells us **how spread out** the outcomes are —
how much they **vary** from the mean.

-   Low variance = outcomes are consistent
-   High variance = outcomes fluctuate more

#### Variance formula for Bernoulli Distribution:

$$
\large \sigma^2 = \text Var(X) = p(1 - p)
$$

-   If *p* = 0 or *p* = 1: the outcome is **always the same**, so
    variance = 0
-   If *p* = 0.5: equal chance of 0 and 1 → **Maximum
    unpredictability**, so variance = 0.25

#### Table: Mean and Variance for Different *p*

<table>
<thead>
<tr>
<th><span class="math inline"><em>p</em></span></th>
<th>Mean (<span class="math inline"><em>μ</em></span>)</th>
<th>Variance (<span
class="math inline"><em>σ</em><sup>2</sup></span>)</th>
</tr>
</thead>
<tbody>
<tr>
<td>0.2</td>
<td>0.2</td>
<td>0.16</td>
</tr>
<tr>
<td>0.5</td>
<td>0.5</td>
<td>0.25</td>
</tr>
<tr>
<td>0.8</td>
<td>0.8</td>
<td>0.16</td>
</tr>
<tr>
<td>1.0</td>
<td>1.0</td>
<td>0.00</td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 56%" />
<col style="width: 31%" />
</colgroup>
<thead>
<tr>
<th>Term</th>
<th>Meaning</th>
<th>Formula</th>
</tr>
</thead>
<tbody>
<tr>
<td>Mean</td>
<td>Long-run average outcome</td>
<td><span class="math inline"><em>μ</em> = <em>p</em></span></td>
</tr>
<tr>
<td>Variance</td>
<td>How much the outcome varies from mean</td>
<td><span
class="math inline"><em>σ</em><sup>2</sup> = <em>p</em>(1 − <em>p</em>)</span></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

## Bernoulli Distribution Plot

![](Bernoulli-Distribution_files/figure-markdown_strict/unnamed-chunk-1-1.png)

![](Bernoulli-Distribution_files/figure-markdown_strict/unnamed-chunk-2-1.png)

Here, each graph shows a different Bernoulli distribution.

-   Left: p = 0.2 (20% chance of success)
-   Center: p = 0.5 (50% chance of success)
-   Right: p = 0.8 (80% chance of success)

#### Key Characteristics

-   **Single trial** with two possible outcomes: 0 and 1
-   Controlled by a **single parameter:*p***
-   Used to model **binary events**
-   Simple and forms the basis for other distributions like Binomial
-   When *p* = 0.5, the distribution is **symmetric**, as **success and
    failure are equal**
-   When *P* ≠ 0.5, the distribution is asymmetric.

#### Simulation of Multiple Bernoulli Trials

    ## sim_data
    ##  0  1 
    ## 71 29

![](Bernoulli-Distribution_files/figure-markdown_strict/unnamed-chunk-3-1.png)

### Connection to Hypothesis Testing

In hypothesis testing, we often test whether the probability of success
equals a specific value:

-   Null Hypothesis *H*<sub>*o*</sub> : *p* = 0.5

-   Alternative Hypothesis *H*<sub>1</sub> : *p* ≠ 0.5

We use test statistics and p-values to decide whether to reject
*H*<sub>*o*</sub>.

#### Applications in Real Life

<table>
<thead>
<tr>
<th>Situation</th>
<th>Bernoulli Outcome</th>
</tr>
</thead>
<tbody>
<tr>
<td>Toss a coin</td>
<td>1 (Heads), 0 (Tails)</td>
</tr>
<tr>
<td>Pass/fail a test</td>
<td>1 (Pass), 0 (Fail)</td>
</tr>
<tr>
<td>Email is spam or not</td>
<td>1 (Spam), 0 (Not spam)</td>
</tr>
<tr>
<td>Customer buys a product or not</td>
<td>1 (Buy), 0 (No buy)</td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

#### Use in Machine Learning

Bernoulli distribution is used to **model binary data** and
**classification tasks**. Here’s how it fits into ML:

#### 1. Binary Classification

In ML, many problems involve predicting **yes/no, spam/not spam,
clicked/not clicked**, etc.

Bernoulli distribution provides the foundation for:

-   **Target variable** (label) in binary classification is modeled as
    ***y* ∼ *B**e**r**n**o**u**l**l**i*(*p*)**
-   **Predicted probabilities** (from models like logistic regression)
    estimate the success probability *p*

#### Example:

Predicting if an email is spam: \* *y* = 1 → spam \* *y* = 0 → not spam

The outcome follows:

*P*(*y* = 1) = *p*, *P*(*y* = 0) = 1 − *p*

#### 2. Bernoulli Naive Bayes Classifier

This ML algorithm **assumes features are binary**, and each follows a
Bernoulli distribution.

Used when: \* Features are presence/absence (e.g., word present in a
document = 1, absent = 0) \* Especially common in **text
classification** (e.g., spam detection)

#### 3. Simulating Binary Labels in ML

If we’re simulating binary outcomes in ML (for testing or synthetic
data), we can use:

    ## y
    ##  0  1 
    ## 74 26

#### 4. Logistic Regression and Bernoulli

In **logistic regression**, the likelihood of the response variable is
modeled using the Bernoulli distribution.

The output is:

-   A probability is:
-   p between 0 and 1
-   Then interpreted as a **Bernoulli trial**

------------------------------------------------------------------------

#### Relation to Binomial Distribution

The **Binomial Distribution** is simply the sum of multiple independent
**Bernoulli trials**.

> Example: Tossing a coin 10 times is a Binomial trial with *n* = 10.
> But each individual toss follows a **Bernoulli distribution**.

------------------------------------------------------------------------

### Limitations & Issues of Bernoulli Distribution

#### 1. Binary Outcomes Only

The Bernoulli distribution **can only handle two outcomes** (0 or 1,
success/failure).

-   Cannot be used for multiclass classification or multi-category data.

-   Use a **multinomial** or **categorical distribution** instead for
    &gt;2 classes.

#### 2. Assumes Fixed Probability

-   The probability of success *p* is assumed to be **constant** across
    trials.

-   In real-life applications, probabilities may change due to:

    -   Time

    -   Context

    -   User behavior

    -   Environment

> In such cases, use models with **varying probabilities**, like
> logistic regression.

#### 4. Not Suitable for Continuous Variables

-   Bernoulli only models **discrete binary data**.

-   It cannot be used for modeling continuous measurements like height,
    weight, or temperature.

> Use distributions like **Normal, Exponential**, etc., for continuous
> data.

#### 5. Limited Information in Single Trial

-   A single Bernoulli trial gives very little data (just 0 or 1).

-   We need many repetitions to estimate meaningful statistics like mean
    or variance.

> Often extended to **Binomial distribution** (sum of multiple Bernoulli
> trials).

#### 6. High Variance for Mid-range p

-   When *p* is near 0.5, the variance *p*(1 − *p*) is highest.

-   This introduces **greater uncertainty** in modeling outcomes, making
    estimation less reliable without large sample sizes.

#### 7. Cannot Capture Feature Interactions

-   In Bernoulli Naive Bayes:

    -   Assumes features are independent given the class label.

    -   Ignores feature interactions.

> Leads to oversimplified models in complex ML tasks.

#### 8. Not Robust to Noise or Outliers

-   Since it only accepts 0 or 1:

    -   Noisy labels (e.g., mislabeled examples) can strongly affect
        model performance.

    -   It’s not flexible enough to accommodate uncertain or fuzzy
        outcomes.

------------------------------------------------------------------------

#### Summary

<table>
<colgroup>
<col style="width: 41%" />
<col style="width: 58%" />
</colgroup>
<thead>
<tr>
<th>Limitation</th>
<th>Why It Matters</th>
</tr>
</thead>
<tbody>
<tr>
<td>Only binary outcomes</td>
<td>Can’t handle multiclass problems</td>
</tr>
<tr>
<td>Fixed success probability</td>
<td>May not reflect real-world variability</td>
</tr>
<tr>
<td>Assumes independent trials</td>
<td>Doesn’t fit time-dependent data</td>
</tr>
<tr>
<td>Not for continuous data</td>
<td>Unsuitable for real-valued features</td>
</tr>
<tr>
<td>Limited info from one trial</td>
<td>Needs many repetitions to be informative</td>
</tr>
<tr>
<td>High variance near <span
class="math inline"><em>p</em> = 0.5</span></td>
<td>Outcomes more uncertain</td>
</tr>
<tr>
<td>Ignores feature interactions</td>
<td>Less accurate ML predictions</td>
</tr>
<tr>
<td>Sensitive to label noise</td>
<td>Errors can distort results significantly</td>
</tr>
</tbody>
</table>
