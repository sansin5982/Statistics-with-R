# Data Types

Data in statistics refers to any set of observations or measurements
that are collected from a particular population or sample. This can
include numerical data, such as measurements of height, weight, or
income, as well as categorical data, such as responses to survey
questions or demographic information.

Data is used in statistics to make inferences or draw conclusions about
the larger population from which the data was collected. This involves
using statistical methods to analyze the data and identify patterns or
relationships between variables.

There are many different types of statistical analyses that can be used
depending on the type of data being analyzed and the research question
being addressed. For example, descriptive statistics can be used to
summarize and describe the main features of a data set, while
inferential statistics can be used to make predictions or test
hypotheses about the population based on the data collected from a
sample.

## Variable

In statistics, a variable is a characteristic or property that can vary
or take on different values among individuals, objects, or events in a
population or sample.Some examples are age, blood pressure, heart rate,
height, gender etc.

## Data Types

Qualitative data and quantitative data are two types of data used in
research, analysis, and statistics.

<img src="Figures/Data type.png" alt="Figure 3.1: Data Types in Statistics" width="50%" />
<p class="caption">
Figure 3.1: Data Types in Statistics
</p>

##### Source: <https://www.studypug.com/statistics-help/classification-of-data>

## Quantitative Data

Quantitative data refers to numerical data that can be measured and
analyzed using statistical methods. Quantitative data can provide
precise and objective information about a particular phenomenon or
population, and can help researchers test hypotheses and make
predictions. For example, age, height, blood pressure, etc. Quantitative
data is further divided into discrete and continuous.

### Discrete variable

Discrete data refers to numerical data that can only take on certain
specific values, typically integers. This means that there are a limited
number of possible values that a discrete variable can take on. Examples
of discrete data include the number of siblings a person has, the number
of cars in a parking lot, and the number of children in a family.

### Continuous variable

Continuous data refers to numerical data that can take on any value
within a range, and can be measured with infinite precision. This means
that there are an infinite number of possible values that a continuous
variable can take on. Examples of continuous data include height,
weight, temperature, and time. Continuous variable is further divided
into interval and ration scale.

#### Interval scale

Interval data are continuous data where the differences between the
values are equal, but there is no true zero point. Examples of interval
data include temperature (measured in Celsius or Fahrenheit), time
(measured in hours or minutes), and IQ scores.

#### Ratio Scale

Ratio data are numerical data where there is a true zero point, and the
ratios between the values are meaningful. Examples of ratio data include
weight, height, age, and income (measured in dollars).

### Qualitative Data

There are some characteristics that cannot be measured as height, weight
and blood pressure. These variables can be categorized only. For
example: gender, ethnicity, race etc. Qualitative data is further
divided into nominal and ordinal.

#### Nominal variable

Nominal data are categorical data that cannot be ranked or ordered.
Examples of nominal data include gender (male or female), race (Asian,
Black, Hispanic, etc.), and favorite color (red, blue, green, etc.).

#### Ordinal variable

Ordinal data are categorical data that can be ranked or ordered.
However, the differences between the ranks are not necessarily equal.
Examples of ordinal data include education level (high school, some
college, Bachelor’s degree, Master’s degree, etc.), income level (low,
middle, high), and satisfaction level (very dissatisfied, somewhat
dissatisfied, neutral, somewhat satisfied, very satisfied).

## Random Variable

A random variable is a mathematical function that assigns a numerical
value to each possible outcome of a random event or experiment. In other
words, it is a variable that takes on different values based on chance
or probability.

Random variables can be discrete or continuous. **Discrete random
variables** take on only a finite or countable set of values, such as
the number of heads that come up in a series of coin tosses.
**Continuous random variables**, on the other hand, can take on any
value within a range, such as the height of individuals in a population.

Random variables are used in statistical analyses to model and describe
the probability distributions of different events or phenomena. They are
often represented using probability density functions or cumulative
distribution functions, which provide information about the likelihood
of different outcomes.

Examples of random variables include the number of cars that pass
through a particular intersection in an hour, the temperature of a room
at a given time, or the number of people who purchase a particular
product in a day.

# Grouped Data: Frequency Distribution

Frequency distribution is a statistical technique used to organize and
summarize data in a clear and concise manner. It involves counting the
number of times each value or category occurs in a dataset and
presenting this information in a tabular form.

Frequency distribution can be applied to both qualitative and
quantitative data. For qualitative data, frequency distribution involves
counting the number of times each category occurs in the data, while for
quantitative data, it involves counting the number of times each value
or range of values occurs in the data.

The information obtained from a frequency distribution can be used to
calculate various measures of central tendency (such as the mean,
median, and mode) and measures of dispersion (such as the range and
standard deviation) for the data.

Frequency distributions can also be presented graphically using various
charts and graphs, such as histograms, bar charts, and pie charts. These
visual representations can help to highlight patterns and trends in the
data and make it easier to understand and interpret.

## Relative frequency

Relative frequency is the proportion or percentage of times that a
particular value or category appears in the data. It is calculated by
dividing the frequency of a value or category by the total number of
observations in the dataset. The result is expressed as a decimal or
percentage. Relative frequency helps to compare the occurrence of
different values or categories in the data.

## Cumulative frequency

Cumulative frequency is the frequency of all values up to a particular
value or category. It is calculated by adding up the frequencies of each
value or category up to the one in question. Cumulative frequency helps
to track the progression of the data as values increase or decrease.

To create a frequency distribution table for weight, we need a dataset
that contains weight measurements. Here’s an example dataset:

weights = \[62, 72, 65, 84, 75, 68, 71, 76, 69, 81, 73, 78, 77, 74, 70,
67, 80, 79, 82, 66\]

We can create a frequency distribution table for weight using the
following steps:

Determine the range of the data by finding the difference between the
maximum and minimum values. In this case, the range is 84 - 62 = 22. 1.
Determine the number of intervals (or bins) to use in the table. A
common rule of thumb is to use 5-20 intervals, depending on the size of
the dataset. For this example, we’ll use 5 intervals. 2. Determine the
width of each interval by dividing the range by the number of intervals
and rounding up to the nearest integer. In this case, the interval width
is 5. 3. Create the frequency distribution table by counting the number
of observations that fall within each interval. 4. Here’s the frequency
distribution table for weight:

<table>
<thead>
<tr class="header">
<th>Weight Interval</th>
<th>Frequency</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>62-66</td>
<td>2</td>
</tr>
<tr class="even">
<td>67-71</td>
<td>4</td>
</tr>
<tr class="odd">
<td>72-76</td>
<td>5</td>
</tr>
<tr class="even">
<td>77-81</td>
<td>5</td>
</tr>
<tr class="odd">
<td>82-86</td>
<td>4</td>
</tr>
</tbody>
</table>

To calculate the values for the relative frequency and cumulative
frequency columns, we can use the following formulas:

-   Relative frequency = frequency / total number of observations
-   Cumulative frequency = sum of frequencies up to and including the
    current interval

Here’s the updated frequency distribution table with the relative and
cumulative frequency columns:

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Weight Interval</th>
<th>Frequency</th>
<th>Relative Frequency</th>
<th>Cumulative Frequency</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>62-66</td>
<td>2</td>
<td>0.1</td>
<td>2</td>
</tr>
<tr class="even">
<td>67-71</td>
<td>4</td>
<td>0.2</td>
<td>6</td>
</tr>
<tr class="odd">
<td>72-76</td>
<td>5</td>
<td>0.25</td>
<td>11</td>
</tr>
<tr class="even">
<td>77-81</td>
<td>5</td>
<td>0.25</td>
<td>16</td>
</tr>
<tr class="odd">
<td>82-86</td>
<td>4</td>
<td>0.2</td>
<td>20</td>
</tr>
</tbody>
</table>

We can see from the table that the majority of the weights fall within
the 72-76 and 77-81 intervals, and the cumulative frequency of 16
indicates that 16 out of the 20 observations fall within those two
intervals.

# Reference:
