<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Probability

The foundation of statistical inference is the theory of probability. It
tells the likelihood of an event occurring. Probability measures the
likelihood that a specific event will occur, expressed as a number
between 0 (impossible) and 1 (certain). An event is likely of unlikely.

------------------------------------------------------------------------

## Frequentist definition

If an experiment is repeated n times under essential identical
conditions, and if the event A occurs m times, then as n grows large,
the **ratio of m/n** approaches to a fixed limit that is probability of
A:

The probability of event A is given by:

$$
\large P(A) = \frac{m}{n}
$$

-   P(A) = Probability of event A

------------------------------------------------------------------------

## Law of large numbers

The Law of Large Numbers is a fundamental concept in probability that
states that as the number of trials or observations increases, the
average of the results obtained from these trials will converge to the
expected value.

Imagine flipping a fair coin multiple times. The expected probability of
getting heads is 0.5. According to the Law of Large Numbers, as you flip
the coin more and more times, the proportion of heads (or tails) should
get closer and closer to 0.5.

Let’s start with 10 flips of a coin.

<img src="Figures/10_coin_flip.jpg" alt="Figure 6.1: 10 coin flips" width="50%" />
<p class="caption">
Figure 6.1: 10 coin flips
</p>

Here is the bar chart illustrating the result of 10 coin flips, with a
noticeable deviation from the expected probability of 0.5.

Now 50 flips of a coin.

<img src="Figures/50_coin flip.webp" alt="Figure 6.2: 50 coin flips" width="50%" />
<p class="caption">
Figure 6.2: 50 coin flips
</p>

Here is the bar chart illustrating the result of 50 coin flips, where
the proportions are closer to the expected 0.5.

Now 1000 flips of a coin.

<img src="Figures/1000_coin_flips.webp" alt="Figure 6.3: 1000 coin flips" width="50%" />
<p class="caption">
Figure 6.3: 1000 coin flips
</p>

Here is the bar chart illustrating the result of 1000 coin flips,
showing how the proportions of heads and tails converge closely to 0.5.

------------------------------------------------------------------------

## Important concepts used in probability

### Event

An **event** in probability theory is a subset of the sample space (the
set of all possible outcomes). It represents a specific outcome or a
group of outcomes of an experiment.

-   Suppose we roll a six-sided die. The sample space is:

*S* = {1, 2, 3, 4, 5, 6}

-   An event could be rolling an even number:

*E* = {2, 4, 6}

-   Another event could be rolling a number greater than 4 :

*F* = {5, 6}

**Formula**: If an event *A* occurs with probability *P*(*A*), then:

$$
\large P(A) = \frac{\text{Number of Favorable Outcomes}}{\text{Total Number of Outcomes}}
$$

-   If we define event *A* as rolling an even number, the probability
    is:
    -   Total even numbers = 3
    -   Total number of outcomes = 6

$$
\large P(A) = \frac{3}{6} = 0.5
$$
—

### Complement

The **complement** of an event *A* (denoted as *A*<sup>*c*</sup> or *Ā*
consists of all outcomes in the sample space that are **not** in *A*.

-   Counting with the die roll:
    -   *A* = Rolling an even number {2, 4, 6}
    -   *A*<sup>*c*</sup> = Not rolling an even number {1, 3, 5}

**Formula**:

$$
\large P(A^c) = 1 - P(A)
$$

**Example**:

If *P*(*A*) = 0.5, here rolling an even number then:

$$
\large P(A^c) = 1 - 0.5 = 0.5
$$
—

## Sample Space

The **sample space** (denoted as *S*) is the set of all possible
outcomes of a random experiment.

**Example**:  
Rolling a six-sided die:

*S* = {1, 2, 3, 4, 5, 6}

Each number represents a possible outcome. An **event** is a subset of
this sample space.

------------------------------------------------------------------------

## Disjoint (Mutually Exclusive) Events

Two events are **disjoint** if they **cannot occur at the same time**.

**Example**:  
- *A* = {2, 4, 6}  
- *B* = {1, 3, 5}

Since *A* ∩ *B* = ∅, the events are disjoint.

**Formula**:

$$
\large P(A \cup B) = P(A) + P(B)
$$

------------------------------------------------------------------------

## Non-Disjoint Events

Two events are **non-disjoint** if they **can occur together** (i.e.,
they have overlapping outcomes).

**Example**:  
- *A* = {4, 5, 6}  
- *B* = {2, 4, 6}

Then:

*A* ∩ *B* = {4, 6}

**Formula**:

$$
\large P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

------------------------------------------------------------------------

## Independent Events

Two events are **independent** if the occurrence of one does **not
affect** the probability of the other.

**Example**:  
- Tossing a coin: *P*(*A*) = Heads = 0.5  
- Rolling a die: $P(B) = \text{6} = \frac{1}{6}$

The result of the coin does not impact the die roll.

**Formula**:

$$
\large P(A \cap B) = P(A) \cdot P(B)
$$

------------------------------------------------------------------------

## Dependent Events

Two events are **dependent** if the occurrence of one **affects** the
probability of the other.

**Example**:  
Drawing two cards from a deck **without replacement**: - Event A: First
card is an Ace  
- Event B: Second card is an Ace given that the first was an Ace

The probability of B depends on what happened in A.

**Formula**:

$$
\large P(A \cap B) = P(A) \cdot P(B|A)
$$

[⬅ Back to Home](../index.md)
