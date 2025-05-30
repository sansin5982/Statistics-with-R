<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Probability Distributions

A **probability distribution** is like a rulebook that tells us how
likely each possible outcome of an experiment is.

Think of it like this: - You roll a die → you want to know how likely
each number is (1 to 6) - You measure height → you want to know how
likely different height ranges are

A probability distribution helps us **map out those chances**.

------------------------------------------------------------------------

## Types of Probability Distributions

## 1. Discrete Probability Distribution

-   Used when outcomes are **countable** (like number of people, dice
    rolls, coin flips).
-   We can list out all the possible outcomes.
-   Each outcome has a specific probability.

### Example: Rolling a Die

-   Outcomes: 1, 2, 3, 4, 5, 6
-   Each has a probability of 1/6

This is a **discrete distribution** because we can count the possible
outcomes.

------------------------------------------------------------------------

### Function: PMF (Probability Mass Function)

PMF tells you the **probability of each exact value**.

------------------------------------------------------------------------

## 2. Continuous Probability Distribution

-   Used when outcomes can be **any value within a range**.
-   You can’t list them all because there are **infinitely many** (like
    1.2, 1.23, 1.234…).
-   Think of things like **height, weight, or temperature**.

### Example: Measuring Height

-   A person’s height could be 160.2 cm or 160.23 cm or 160.234 cm, etc.
-   You can’t give a probability to **one exact value**.
-   Instead, you find the probability **within a range**, like 160–170
    cm.

### Function: PDF (Probability Density Function)

PDF tells you the **density of probability** across a range of values.

------------------------------------------------------------------------

#### Summary Table

<table style="width:100%;">
<colgroup>
<col style="width: 13%" />
<col style="width: 28%" />
<col style="width: 11%" />
<col style="width: 46%" />
</colgroup>
<thead>
<tr>
<th>Type</th>
<th>Use Case Examples</th>
<th>Function</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Discrete</td>
<td>Dice rolls, coin flips</td>
<td>PMF</td>
<td>Probability for <strong>each value</strong></td>
</tr>
<tr>
<td>Continuous</td>
<td>Height, weight, age</td>
<td>PDF</td>
<td>Probability for a <strong>range of values</strong></td>
</tr>
</tbody>
</table>

#### Final Note

-   Use **discrete** distributions when you can **count the outcomes**.
-   Use **continuous** distributions when the outcomes can take **any
    value in a range**.
-   Both are tools to help you understand how likely something is to
    happen.
