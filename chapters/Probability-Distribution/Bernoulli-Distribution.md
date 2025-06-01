<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Bernoulli Distribution

The **Bernoulli Distribution** is one of the **simplest discrete
probability distributions**. It models situations where there are only
**two possible outcomes** — typically called “success” and “failure”.

------------------------------------------------------------------------

#### Real-Life Examples

-   Tossing a coin (Heads = 1, Tails = 0)  
-   Checking if a light bulb is working (Yes = 1, No = 0)  
-   A customer buying a product (Buys = 1, Doesn’t buy = 0)

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

Where: - *p* is the probability of success (i.e., getting a 1)  
- 1 − *p* is the probability of failure (i.e., getting a 0)

------------------------------------------------------------------------

### Properties

<table>
<thead>
<tr>
<th>Property</th>
<th>Formula</th>
</tr>
</thead>
<tbody>
<tr>
<td>Mean</td>
<td><span class="math inline"><em>μ</em> = <em>p</em></span></td>
</tr>
<tr>
<td>Variance</td>
<td><span
class="math inline"><em>σ</em><sup>2</sup> = <em>p</em>(1 − <em>p</em>)</span></td>
</tr>
<tr>
<td>Support</td>
<td>0 or 1</td>
</tr>
<tr>
<td>Type</td>
<td>Discrete</td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

## Bernoulli Distribution Plot

![](Bernoulli-Distribution_files/figure-markdown_strict/unnamed-chunk-1-1.png)

#### Key Characteristics

-   **Single trial** with two possible outcomes: 0 and 1
-   Controlled by a **single parameter:*p***
-   Used to model **binary events**
-   Simple and forms the basis for other distributions like Binomial

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

#### Limitations

-   Only works for **binary outcomes**
-   Can’t handle **more than two categories**
-   Assumes each trial is **independent**

#### Relation to Binomial Distribution

The **Binomial Distribution** is simply the sum of multiple independent
**Bernoulli trials**.

> Example: Tossing a coin 10 times is a Binomial trial with *n* = 10.
> But each individual toss follows a **Bernoulli distribution**.

#### Summary

-   Bernoulli distribution is the simplest discrete probability model
-   Used when the outcome is binary: success/failure, yes/no, 1/0
-   Defined by a single parameter *p*
-   Foundation of the Binomial distribution
