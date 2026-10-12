---
title: "Chapter 7: Tables and Frequency Distributions"
subtitle: "Organizing Biological Data Before Statistical Analysis"
author: "Sandeep Singh"
output:
  github_document:
    toc: true
    toc_depth: 3
    fig_width: 8
    fig_height: 5
    df_print: kable
    preserve_yaml: true
---

Chapter 7: Tables and Frequency Distributions
================
Sandeep Singh

- [1. Introduction](#1-introduction)
- [2. A Small Biological Dataset](#2-a-small-biological-dataset)
- [3. What Is a Frequency
  Distribution?](#3-what-is-a-frequency-distribution)
- [4. One-Way Frequency Tables](#4-one-way-frequency-tables)
  - [4.1 Counts with `table()`](#41-counts-with-table)
  - [4.2 Convert the table to a data
    frame](#42-convert-the-table-to-a-data-frame)
  - [4.3 Relative frequencies and
    percentages](#43-relative-frequencies-and-percentages)
- [5. Category Order and Factors](#5-category-order-and-factors)
  - [5.1 Showing categories with zero
    observations](#51-showing-categories-with-zero-observations)
- [6. Missing Values in Frequency
  Tables](#6-missing-values-in-frequency-tables)
  - [6.1 Missing as a value versus missing as a
    category](#61-missing-as-a-value-versus-missing-as-a-category)
  - [6.2 A complete missingness table](#62-a-complete-missingness-table)
- [7. Cumulative Frequency](#7-cumulative-frequency)
- [8. Numerical Data: Ungrouped Frequency
  Tables](#8-numerical-data-ungrouped-frequency-tables)
- [9. Grouped Frequency
  Distributions](#9-grouped-frequency-distributions)
  - [9.1 Create age groups with `cut()`](#91-create-age-groups-with-cut)
  - [9.2 Understanding interval
    boundaries](#92-understanding-interval-boundaries)
- [10. Choosing the Number and Width of
  Classes](#10-choosing-the-number-and-width-of-classes)
  - [10.1 Sturges’ rule](#101-sturges-rule)
  - [10.2 Freedman–Diaconis rule](#102-freedmandiaconis-rule)
- [11. Bar Charts for Categorical
  Data](#11-bar-charts-for-categorical-data)
  - [11.1 Counts or percentages?](#111-counts-or-percentages)
- [12. Histograms for Continuous
  Data](#12-histograms-for-continuous-data)
  - [12.1 Bar chart versus histogram](#121-bar-chart-versus-histogram)
- [13. Frequency Polygon and Cumulative
  Distribution](#13-frequency-polygon-and-cumulative-distribution)
  - [13.1 Empirical cumulative distribution
    function](#131-empirical-cumulative-distribution-function)
- [14. Two-Way Contingency Tables](#14-two-way-contingency-tables)
  - [14.1 Disease status by recorded
    sex](#141-disease-status-by-recorded-sex)
  - [14.2 Add marginal totals](#142-add-marginal-totals)
  - [14.3 Create a contingency table with
    `xtabs()`](#143-create-a-contingency-table-with-xtabs)
- [15. Joint, Row and Column
  Proportions](#15-joint-row-and-column-proportions)
  - [15.1 Joint proportions](#151-joint-proportions)
  - [15.2 Row proportions](#152-row-proportions)
  - [15.3 Column proportions](#153-column-proportions)
- [16. Visualizing a Two-Way Table](#16-visualizing-a-two-way-table)
- [17. Three-Way and Multi-Way
  Tables](#17-three-way-and-multi-way-tables)
- [18. Counts, Proportions, Percentages, Ratios and
  Rates](#18-counts-proportions-percentages-ratios-and-rates)
  - [18.1 Example calculations](#181-example-calculations)
- [19. Genotype and Allele Frequency
  Tables](#19-genotype-and-allele-frequency-tables)
  - [19.1 Genotype frequencies](#191-genotype-frequencies)
  - [19.2 Allele counts](#192-allele-counts)
  - [19.3 Genotype by disease status](#193-genotype-by-disease-status)
- [20. Bioinformatics Count Tables](#20-bioinformatics-count-tables)
  - [20.1 RNA-seq count matrix](#201-rna-seq-count-matrix)
  - [20.2 Variant consequence counts](#202-variant-consequence-counts)
- [21. Zero Counts, Sparse Tables and Small
  Numbers](#21-zero-counts-sparse-tables-and-small-numbers)
- [22. Creating a Clean Summary
  Table](#22-creating-a-clean-summary-table)
  - [22.1 Add a display column](#221-add-a-display-column)
- [23. An Introductory “Table 1”](#23-an-introductory-table-1)
- [24. Integrated Case Study: Sequencing Quality-Control
  Summary](#24-integrated-case-study-sequencing-quality-control-summary)
  - [24.1 Scientific setting](#241-scientific-setting)
  - [24.2 Simulate the sample-level
    data](#242-simulate-the-sample-level-data)
  - [24.3 Overall QC frequency](#243-overall-qc-frequency)
  - [24.4 QC by centre](#244-qc-by-centre)
  - [24.5 QC by disease group and
    batch](#245-qc-by-disease-group-and-batch)
  - [24.6 Plot centre-specific failure
    percentages](#246-plot-centre-specific-failure-percentages)
- [25. Common Mistakes](#25-common-mistakes)
  - [Mistake 1: Reporting percentages without
    counts](#mistake-1-reporting-percentages-without-counts)
  - [Mistake 2: Ignoring missing
    values](#mistake-2-ignoring-missing-values)
  - [Mistake 3: Using the wrong
    denominator](#mistake-3-using-the-wrong-denominator)
  - [Mistake 4: Treating ordinal categories as
    nominal](#mistake-4-treating-ordinal-categories-as-nominal)
  - [Mistake 5: Using overlapping
    intervals](#mistake-5-using-overlapping-intervals)
  - [Mistake 6: Choosing bins to create a desired visual
    impression](#mistake-6-choosing-bins-to-create-a-desired-visual-impression)
  - [Mistake 7: Confusing a bar chart with a
    histogram](#mistake-7-confusing-a-bar-chart-with-a-histogram)
  - [Mistake 8: Treating transcript counts as variant
    counts](#mistake-8-treating-transcript-counts-as-variant-counts)
  - [Mistake 9: Interpreting descriptive differences as
    proof](#mistake-9-interpreting-descriptive-differences-as-proof)
  - [Mistake 10: Calculating prevalence from a case-control
    sample](#mistake-10-calculating-prevalence-from-a-case-control-sample)
- [26. Practical Reporting Checklist](#26-practical-reporting-checklist)
- [27. Chapter Summary](#27-chapter-summary)
- [28. Check Your Understanding](#28-check-your-understanding)
- [29. R Exercises](#29-r-exercises)
  - [Exercise 1: One-way table](#exercise-1-one-way-table)
  - [Exercise 2: Ordered categories](#exercise-2-ordered-categories)
  - [Exercise 3: Missingness](#exercise-3-missingness)
  - [Exercise 4: Grouped ages](#exercise-4-grouped-ages)
  - [Exercise 5: Histogram bins](#exercise-5-histogram-bins)
  - [Exercise 6: Two-way table](#exercise-6-two-way-table)
  - [Exercise 7: Genotype frequencies](#exercise-7-genotype-frequencies)
  - [Exercise 8: Variant annotation](#exercise-8-variant-annotation)
  - [Exercise 9: QC summary function](#exercise-9-qc-summary-function)
  - [Exercise 10: Sparse table](#exercise-10-sparse-table)
- [30. Mini-Project: Pathogen Genomic Surveillance
  Summary](#30-mini-project-pathogen-genomic-surveillance-summary)
- [31. Glossary](#31-glossary)
- [32. References](#32-references)
- [33. Reproducibility Information](#33-reproducibility-information)

<script>
window.MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']],
    displayMath: [['$$', '$$'], ['\\[', '\\]']],
    processEscapes: true
  }
};
</script>

<script
  id="MathJax-script"
  async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

<style>
table.chapter-table {
  border-collapse: collapse;
  display: block;
  width: 100%;
  margin: 1rem 0;
  overflow-x: auto;
}
&#10;table.chapter-table th,
table.chapter-table td {
  border: 1px solid #d0d7de;
  padding: 0.45rem 0.65rem;
  text-align: left;
  vertical-align: top;
}
&#10;table.chapter-table th {
  background-color: #f6f8fa;
  font-weight: 600;
}
&#10;table.chapter-table caption {
  margin-bottom: 0.5rem;
  font-weight: 600;
  text-align: left;
}
</style>

# 1. Introduction

Raw biological data are often difficult to understand by looking at
individual rows. A dataset may contain hundreds of patients, thousands
of genes or millions of sequence variants. Before calculating advanced
statistics, we need a compact description of what the data contain.

**Tables** and **frequency distributions** answer basic but essential
questions:

- How many observations belong to each group?
- What percentage of samples passed quality control?
- How are ages or biomarker values distributed?
- Are genotype frequencies different between cases and controls?
- How much data is missing?
- Are some categories rare or absent?

These summaries are usually the first formal step in exploratory data
analysis.

> **A good frequency table converts a column of raw values into a
> scientific summary without hiding the denominator.**

# 2. A Small Biological Dataset

We will use a simulated clinical-genomics dataset throughout the
chapter. Each row represents one participant.

``` r
set.seed(123)

n <- 120

clinical_data <- data.frame(
  patient_id = sprintf("P%03d", seq_len(n)),
  disease_status = sample(
    c("Control", "Case"), n, replace = TRUE,
    prob = c(0.58, 0.42)
  ),
  recorded_sex = sample(
    c("Female", "Male"), n, replace = TRUE,
    prob = c(0.53, 0.47)
  ),
  age_years = round(rnorm(n, mean = 51, sd = 14)),
  expression_group = sample(
    c("Low", "Medium", "High", NA), n, replace = TRUE,
    prob = c(0.25, 0.43, 0.27, 0.05)
  ),
  genotype = sample(
    c("AA", "AG", "GG", NA), n, replace = TRUE,
    prob = c(0.48, 0.39, 0.10, 0.03)
  ),
  qc_status = sample(
    c("Pass", "Fail"), n, replace = TRUE,
    prob = c(0.90, 0.10)
  ),
  stringsAsFactors = FALSE
)

# Cases have a modestly higher simulated biomarker value
clinical_data$biomarker <- round(
  rlnorm(
    n,
    meanlog = log(4.5) + 0.18 * (clinical_data$disease_status == "Case"),
    sdlog = 0.32
  ),
  2
)

print_html_table(
  head(clinical_data),
  caption = "First six participants in the simulated clinical-genomics dataset."
)
```

<table class="chapter-table">

<caption>

First six participants in the simulated clinical-genomics dataset.
</caption>

<thead>

<tr>

<th style="text-align:left;">

patient id
</th>

<th style="text-align:left;">

disease status
</th>

<th style="text-align:left;">

recorded sex
</th>

<th style="text-align:right;">

age years
</th>

<th style="text-align:left;">

expression group
</th>

<th style="text-align:left;">

genotype
</th>

<th style="text-align:left;">

qc status
</th>

<th style="text-align:right;">

biomarker
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

P001
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

53
</td>

<td style="text-align:left;">

Medium
</td>

<td style="text-align:left;">

AA
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

7.95
</td>

</tr>

<tr>

<td style="text-align:left;">

P002
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

38
</td>

<td style="text-align:left;">

Low
</td>

<td style="text-align:left;">

AG
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

5.90
</td>

</tr>

<tr>

<td style="text-align:left;">

P003
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

44
</td>

<td style="text-align:left;">

Medium
</td>

<td style="text-align:left;">

AA
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

4.69
</td>

</tr>

<tr>

<td style="text-align:left;">

P004
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

47
</td>

<td style="text-align:left;">

High
</td>

<td style="text-align:left;">

AA
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

8.09
</td>

</tr>

<tr>

<td style="text-align:left;">

P005
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

77
</td>

<td style="text-align:left;">

Low
</td>

<td style="text-align:left;">

AA
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

4.28
</td>

</tr>

<tr>

<td style="text-align:left;">

P006
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

42
</td>

<td style="text-align:left;">

Medium
</td>

<td style="text-align:left;">

AG
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

3.90
</td>

</tr>

</tbody>

</table>

This is **simulated educational data**. It does not describe real
patients and should not be used for clinical conclusions.

# 3. What Is a Frequency Distribution?

A **frequency distribution** shows how observations are distributed
across values or categories.

Suppose 20 tissue samples have the following quality-control results:

- 15 passed;
- 3 failed; and
- 2 were not assessed.

The values 15, 3 and 2 are **absolute frequencies**, usually written as
$f_i$.

If the total number of observations is $n$, the **relative frequency**
of category $i$ is:

$$r_i = \frac{f_i}{n}.$$

The percentage is:

$$p_i = \frac{f_i}{n} \times 100.$$

| QC result    | Frequency | Relative frequency | Percentage |
|--------------|----------:|-------------------:|-----------:|
| Pass         |        15 |               0.75 |        75% |
| Fail         |         3 |               0.15 |        15% |
| Not assessed |         2 |               0.10 |        10% |
| Total        |        20 |               1.00 |       100% |

Always state the denominator. Saying “15 samples passed” has a different
meaning if 20 samples were tested than if 200 were tested.

# 4. One-Way Frequency Tables

A **one-way table** summarizes one categorical variable.

## 4.1 Counts with `table()`

``` r
disease_counts <- table(clinical_data$disease_status)
print_html_table(
  disease_counts,
  caption = "Disease-status frequency counts."
)
```

<table class="chapter-table">

<caption>

Disease-status frequency counts.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Case
</td>

<td style="text-align:right;">

51
</td>

</tr>

<tr>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

69
</td>

</tr>

</tbody>

</table>

`table()` counts how many times each category appears.

## 4.2 Convert the table to a data frame

A data frame is convenient when we want to add proportions or rename
columns.

``` r
disease_frequency <- data.frame(
  Disease_status = names(disease_counts),
  Frequency = as.vector(disease_counts),
  stringsAsFactors = FALSE
)

print_html_table(
  disease_frequency,
  caption = "Disease-status frequency table."
)
```

<table class="chapter-table">

<caption>

Disease-status frequency table.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Disease status
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Case
</td>

<td style="text-align:right;">

51
</td>

</tr>

<tr>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

69
</td>

</tr>

</tbody>

</table>

## 4.3 Relative frequencies and percentages

``` r
disease_frequency$Proportion <- disease_frequency$Frequency /
  sum(disease_frequency$Frequency)

disease_frequency$Percentage <- 100 * disease_frequency$Proportion

disease_frequency$Proportion <- round(disease_frequency$Proportion, 3)
disease_frequency$Percentage <- round(disease_frequency$Percentage, 1)

print_html_table(
  disease_frequency,
  caption = "Disease-status counts, proportions and percentages."
)
```

<table class="chapter-table">

<caption>

Disease-status counts, proportions and percentages.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Disease status
</th>

<th style="text-align:right;">

Frequency
</th>

<th style="text-align:right;">

Proportion
</th>

<th style="text-align:right;">

Percentage
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Case
</td>

<td style="text-align:right;">

51
</td>

<td style="text-align:right;">

0.425
</td>

<td style="text-align:right;">

42.5
</td>

</tr>

<tr>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

69
</td>

<td style="text-align:right;">

0.575
</td>

<td style="text-align:right;">

57.5
</td>

</tr>

</tbody>

</table>

The same relative frequencies can be calculated directly:

``` r
print_html_table(
  prop.table(disease_counts),
  caption = "Disease-status relative frequencies."
)
```

<table class="chapter-table">

<caption>

Disease-status relative frequencies.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Case
</td>

<td style="text-align:right;">

0.425
</td>

</tr>

<tr>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

0.575
</td>

</tr>

</tbody>

</table>

Do not round values too early. Calculate with full precision, then round
only for display.

# 5. Category Order and Factors

Character categories are often displayed alphabetically. Alphabetical
order is not always scientifically meaningful.

For gene-expression categories, the desired order is usually:

> Low $\rightarrow$ Medium $\rightarrow$ High

Convert the variable to an ordered factor:

``` r
clinical_data$expression_group <- factor(
  clinical_data$expression_group,
  levels = c("Low", "Medium", "High"),
  ordered = TRUE
)

print_html_table(
  table(clinical_data$expression_group),
  caption = "Ordered gene-expression categories."
)
```

<table class="chapter-table">

<caption>

Ordered gene-expression categories.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Low
</td>

<td style="text-align:right;">

34
</td>

</tr>

<tr>

<td style="text-align:left;">

Medium
</td>

<td style="text-align:right;">

50
</td>

</tr>

<tr>

<td style="text-align:left;">

High
</td>

<td style="text-align:right;">

30
</td>

</tr>

</tbody>

</table>

The factor levels control the order in tables, models and many plots.

## 5.1 Showing categories with zero observations

If a biologically possible category is absent from a sample, it can
still be useful to display it.

``` r
response <- factor(
  c("Complete", "Partial", "Complete", "Partial"),
  levels = c("Complete", "Partial", "No response")
)

print_html_table(
  table(response),
  caption = "Response categories including an unobserved level."
)
```

<table class="chapter-table">

<caption>

Response categories including an unobserved level.
</caption>

<thead>

<tr>

<th style="text-align:left;">

response
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Complete
</td>

<td style="text-align:right;">

2
</td>

</tr>

<tr>

<td style="text-align:left;">

Partial
</td>

<td style="text-align:right;">

2
</td>

</tr>

<tr>

<td style="text-align:left;">

No response
</td>

<td style="text-align:right;">

0
</td>

</tr>

</tbody>

</table>

A zero count means the category was defined but not observed. It does
not prove that the category is impossible in the population.

# 6. Missing Values in Frequency Tables

By default, `table()` excludes `NA` values. This can silently change the
denominator.

``` r
# Default: missing genotypes are not displayed
print_html_table(
  table(clinical_data$genotype),
  caption = "Genotype frequencies excluding missing values."
)
```

<table class="chapter-table">

<caption>

Genotype frequencies excluding missing values.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

AA
</td>

<td style="text-align:right;">

59
</td>

</tr>

<tr>

<td style="text-align:left;">

AG
</td>

<td style="text-align:right;">

49
</td>

</tr>

<tr>

<td style="text-align:left;">

GG
</td>

<td style="text-align:right;">

9
</td>

</tr>

</tbody>

</table>

``` r
# Display missing values explicitly
print_html_table(
  table(clinical_data$genotype, useNA = "ifany"),
  caption = "Genotype frequencies including missing values."
)
```

<table class="chapter-table">

<caption>

Genotype frequencies including missing values.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

AA
</td>

<td style="text-align:right;">

59
</td>

</tr>

<tr>

<td style="text-align:left;">

AG
</td>

<td style="text-align:right;">

49
</td>

</tr>

<tr>

<td style="text-align:left;">

GG
</td>

<td style="text-align:right;">

9
</td>

</tr>

<tr>

<td style="text-align:left;">

NA
</td>

<td style="text-align:right;">

3
</td>

</tr>

</tbody>

</table>

The `useNA` argument can be:

- `"no"`: exclude missing values;
- `"ifany"`: display missing values only if they exist; or
- `"always"`: always display an `NA` category.

## 6.1 Missing as a value versus missing as a category

`NA` means the value is unknown or unavailable. The text `"Unknown"` is
an ordinary category. They are not automatically equivalent.

For example:

- a genotype may be missing because the assay failed;
- ancestry may be recorded as “Not reported” because the participant
  chose not to answer;
- a treatment may be “Not applicable” for a control group.

Preserve these distinctions when they matter scientifically.

## 6.2 A complete missingness table

``` r
missing_summary <- data.frame(
  Variable = names(clinical_data),
  Missing_n = vapply(clinical_data, function(x) sum(is.na(x)), integer(1)),
  stringsAsFactors = FALSE
)

missing_summary$Missing_percent <- round(
  100 * missing_summary$Missing_n / nrow(clinical_data),
  1
)

print_html_table(
  missing_summary,
  caption = "Missing observations by variable."
)
```

<table class="chapter-table">

<caption>

Missing observations by variable.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Variable
</th>

<th style="text-align:right;">

Missing n
</th>

<th style="text-align:right;">

Missing percent
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

patient_id
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

0.0
</td>

</tr>

<tr>

<td style="text-align:left;">

disease_status
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

0.0
</td>

</tr>

<tr>

<td style="text-align:left;">

recorded_sex
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

0.0
</td>

</tr>

<tr>

<td style="text-align:left;">

age_years
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

0.0
</td>

</tr>

<tr>

<td style="text-align:left;">

expression_group
</td>

<td style="text-align:right;">

6
</td>

<td style="text-align:right;">

5.0
</td>

</tr>

<tr>

<td style="text-align:left;">

genotype
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

2.5
</td>

</tr>

<tr>

<td style="text-align:left;">

qc_status
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

0.0
</td>

</tr>

<tr>

<td style="text-align:left;">

biomarker
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

0.0
</td>

</tr>

</tbody>

</table>

This describes the amount of missingness, not its cause. Patterns and
mechanisms of missing data will be studied later.

# 7. Cumulative Frequency

A **cumulative frequency** is a running total. It is meaningful only
when categories have a natural order.

Consider disease stage I, II, III and IV. Cumulative frequency at stage
II means the number of observations at stage I **or** stage II.

``` r
stage <- factor(
  c("I", "II", "II", "III", "I", "IV", "III", "II", "III", "I"),
  levels = c("I", "II", "III", "IV"),
  ordered = TRUE
)

stage_counts <- table(stage)

stage_distribution <- data.frame(
  Stage = names(stage_counts),
  Frequency = as.vector(stage_counts),
  Cumulative_frequency = cumsum(as.vector(stage_counts)),
  Cumulative_percent = round(100 * cumsum(as.vector(stage_counts)) /
                               sum(stage_counts), 1),
  stringsAsFactors = FALSE
)

print_html_table(
  stage_distribution,
  caption = "Disease-stage frequencies and cumulative frequencies."
)
```

<table class="chapter-table">

<caption>

Disease-stage frequencies and cumulative frequencies.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Stage
</th>

<th style="text-align:right;">

Frequency
</th>

<th style="text-align:right;">

Cumulative frequency
</th>

<th style="text-align:right;">

Cumulative percent
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

I
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

30
</td>

</tr>

<tr>

<td style="text-align:left;">

II
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

6
</td>

<td style="text-align:right;">

60
</td>

</tr>

<tr>

<td style="text-align:left;">

III
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

9
</td>

<td style="text-align:right;">

90
</td>

</tr>

<tr>

<td style="text-align:left;">

IV
</td>

<td style="text-align:right;">

1
</td>

<td style="text-align:right;">

10
</td>

<td style="text-align:right;">

100
</td>

</tr>

</tbody>

</table>

Cumulative frequency is not meaningful for unordered categories such as
blood type A, B, AB and O because no natural “up to” order exists.

# 8. Numerical Data: Ungrouped Frequency Tables

For discrete numerical variables with relatively few possible values,
each value can be counted separately.

Example: number of antibiotic-resistant genes found in each bacterial
isolate.

``` r
set.seed(456)
resistance_gene_count <- rpois(80, lambda = 3)

resistance_table <- table(resistance_gene_count)

resistance_distribution <- data.frame(
  Gene_count = as.integer(names(resistance_table)),
  Frequency = as.vector(resistance_table),
  stringsAsFactors = FALSE
)

resistance_distribution$Percentage <- round(
  100 * resistance_distribution$Frequency /
    sum(resistance_distribution$Frequency),
  1
)

resistance_distribution$Cumulative_frequency <- cumsum(
  resistance_distribution$Frequency
)

print_html_table(
  resistance_distribution,
  caption = "Distribution of antibiotic-resistance gene counts."
)
```

<table class="chapter-table">

<caption>

Distribution of antibiotic-resistance gene counts.
</caption>

<thead>

<tr>

<th style="text-align:right;">

Gene count
</th>

<th style="text-align:right;">

Frequency
</th>

<th style="text-align:right;">

Percentage
</th>

<th style="text-align:right;">

Cumulative frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

3.8
</td>

<td style="text-align:right;">

3
</td>

</tr>

<tr>

<td style="text-align:right;">

1
</td>

<td style="text-align:right;">

9
</td>

<td style="text-align:right;">

11.2
</td>

<td style="text-align:right;">

12
</td>

</tr>

<tr>

<td style="text-align:right;">

2
</td>

<td style="text-align:right;">

22
</td>

<td style="text-align:right;">

27.5
</td>

<td style="text-align:right;">

34
</td>

</tr>

<tr>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

19
</td>

<td style="text-align:right;">

23.8
</td>

<td style="text-align:right;">

53
</td>

</tr>

<tr>

<td style="text-align:right;">

4
</td>

<td style="text-align:right;">

9
</td>

<td style="text-align:right;">

11.2
</td>

<td style="text-align:right;">

62
</td>

</tr>

<tr>

<td style="text-align:right;">

5
</td>

<td style="text-align:right;">

8
</td>

<td style="text-align:right;">

10.0
</td>

<td style="text-align:right;">

70
</td>

</tr>

<tr>

<td style="text-align:right;">

6
</td>

<td style="text-align:right;">

8
</td>

<td style="text-align:right;">

10.0
</td>

<td style="text-align:right;">

78
</td>

</tr>

<tr>

<td style="text-align:right;">

7
</td>

<td style="text-align:right;">

1
</td>

<td style="text-align:right;">

1.2
</td>

<td style="text-align:right;">

79
</td>

</tr>

<tr>

<td style="text-align:right;">

8
</td>

<td style="text-align:right;">

1
</td>

<td style="text-align:right;">

1.2
</td>

<td style="text-align:right;">

80
</td>

</tr>

</tbody>

</table>

An ungrouped table preserves exact values. It becomes unwieldy when a
variable has many distinct values, such as age, blood pressure or gene
expression.

# 9. Grouped Frequency Distributions

A **grouped frequency distribution** divides numerical values into
intervals called **classes** or **bins**.

Example age groups:

- 18–29 years;
- 30–39 years;
- 40–49 years;
- 50–59 years;
- 60–69 years; and
- 70 years or older.

Each interval has:

- a lower boundary;
- an upper boundary;
- a class width; and
- a frequency.

## 9.1 Create age groups with `cut()`

``` r
age_breaks <- c(-Inf, 29, 39, 49, 59, 69, Inf)
age_labels <- c("18-29", "30-39", "40-49", "50-59", "60-69", "70+")

clinical_data$age_group <- cut(
  clinical_data$age_years,
  breaks = age_breaks,
  labels = age_labels,
  right = TRUE
)

age_counts <- table(clinical_data$age_group, useNA = "ifany")

age_distribution <- data.frame(
  Age_group = names(age_counts),
  Frequency = as.vector(age_counts),
  stringsAsFactors = FALSE
)

age_distribution$Percentage <- round(
  100 * age_distribution$Frequency / sum(age_distribution$Frequency),
  1
)

age_distribution$Cumulative_frequency <- cumsum(age_distribution$Frequency)
age_distribution$Cumulative_percent <- round(
  100 * age_distribution$Cumulative_frequency /
    sum(age_distribution$Frequency),
  1
)

print_html_table(
  age_distribution,
  caption = "Grouped age-frequency distribution."
)
```

<table class="chapter-table">

<caption>

Grouped age-frequency distribution.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Age group
</th>

<th style="text-align:right;">

Frequency
</th>

<th style="text-align:right;">

Percentage
</th>

<th style="text-align:right;">

Cumulative frequency
</th>

<th style="text-align:right;">

Cumulative percent
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

18-29
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

2.5
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

2.5
</td>

</tr>

<tr>

<td style="text-align:left;">

30-39
</td>

<td style="text-align:right;">

22
</td>

<td style="text-align:right;">

18.3
</td>

<td style="text-align:right;">

25
</td>

<td style="text-align:right;">

20.8
</td>

</tr>

<tr>

<td style="text-align:left;">

40-49
</td>

<td style="text-align:right;">

37
</td>

<td style="text-align:right;">

30.8
</td>

<td style="text-align:right;">

62
</td>

<td style="text-align:right;">

51.7
</td>

</tr>

<tr>

<td style="text-align:left;">

50-59
</td>

<td style="text-align:right;">

29
</td>

<td style="text-align:right;">

24.2
</td>

<td style="text-align:right;">

91
</td>

<td style="text-align:right;">

75.8
</td>

</tr>

<tr>

<td style="text-align:left;">

60-69
</td>

<td style="text-align:right;">

18
</td>

<td style="text-align:right;">

15.0
</td>

<td style="text-align:right;">

109
</td>

<td style="text-align:right;">

90.8
</td>

</tr>

<tr>

<td style="text-align:left;">

70+
</td>

<td style="text-align:right;">

11
</td>

<td style="text-align:right;">

9.2
</td>

<td style="text-align:right;">

120
</td>

<td style="text-align:right;">

100.0
</td>

</tr>

</tbody>

</table>

## 9.2 Understanding interval boundaries

With `right = TRUE`, intervals are right-closed. For example, `(29, 39]`
contains values greater than 29 and less than or equal to 39.

With `right = FALSE`, `[30, 40)` contains values greater than or equal
to 30 and less than 40.

``` r
test_ages <- c(29, 30, 39, 40)

print_html_table(data.frame(
  Age = test_ages,
  Right_closed = cut(test_ages, breaks = c(20, 30, 40, 50),
                     right = TRUE, include.lowest = TRUE),
  Left_closed = cut(test_ages, breaks = c(20, 30, 40, 50),
                    right = FALSE, include.lowest = TRUE)
), caption = "Comparison of right-closed and left-closed intervals.")
```

<table class="chapter-table">

<caption>

Comparison of right-closed and left-closed intervals.
</caption>

<thead>

<tr>

<th style="text-align:right;">

Age
</th>

<th style="text-align:left;">

Right closed
</th>

<th style="text-align:left;">

Left closed
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:right;">

29
</td>

<td style="text-align:left;">

\[20,30\]
</td>

<td style="text-align:left;">

\[20,30)
</td>

</tr>

<tr>

<td style="text-align:right;">

30
</td>

<td style="text-align:left;">

\[20,30\]
</td>

<td style="text-align:left;">

\[30,40) \]
</td>

<td style="text-align:left;">

\[30,40) \]
</td>

<td style="text-align:left;">

\[40,50\]
</td>

</tr>

</tbody>

</table>

State boundary rules clearly. Ambiguous labels such as “20–30” can make
it unclear where age 30 belongs.

# 10. Choosing the Number and Width of Classes

Too few classes hide important structure. Too many classes produce a
noisy summary.

There is no single correct choice, but common rules provide starting
points.

## 10.1 Sturges’ rule

For a sample of size $n$:

$$k = \left\lceil \log_2(n) + 1 \right\rceil,$$

where $k$ is the suggested number of classes.

``` r
n_observations <- sum(!is.na(clinical_data$biomarker))
k_sturges <- ceiling(log2(n_observations) + 1)
k_sturges
```

    ## [1] 8

## 10.2 Freedman–Diaconis rule

The Freedman–Diaconis class width is:

$$h = 2 \times IQR(x) \times n^{-1/3}.$$

It uses the interquartile range and is less sensitive to extreme values
than a rule based on the full range.

``` r
x <- clinical_data$biomarker
x <- x[!is.na(x)]

fd_width <- 2 * IQR(x) / length(x)^(1 / 3)
fd_width
```

    ## [1] 0.9346317

``` r
fd_breaks <- pretty(range(x),
                    n = ceiling(diff(range(x)) / fd_width))
fd_breaks
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10 11

Rules are guides. Class boundaries should also be interpretable.
Clinically meaningful cut-offs may be preferable when the goal is
clinical classification rather than exploring distribution shape.

# 11. Bar Charts for Categorical Data

A bar chart displays category frequencies. Bars are separated because
the categories are distinct.

``` r
barplot(
  disease_counts,
  col = c("#66C2A5", "#FC8D62"),
  border = NA,
  ylab = "Number of participants",
  xlab = "Disease status",
  main = "Disease-status frequency"
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_07_Tables_and_Frequency_Distributions_files/figure-gfm/disease-bar-chart-1.png" alt="Frequency of simulated disease status. The denominator is 120 participants." width="85%" />
<p class="caption">

Frequency of simulated disease status. The denominator is 120
participants.
</p>

</div>

## 11.1 Counts or percentages?

Use counts when actual sample size matters. Use percentages when
comparing groups of different sizes. Often the clearest report includes
both:

> Case: 49/120 (40.8%)

Avoid a percentage without its denominator.

# 12. Histograms for Continuous Data

A histogram divides a numerical scale into intervals. Adjacent bars
touch because the intervals are continuous.

``` r
hist(
  clinical_data$biomarker,
  breaks = "FD",
  col = "#80B1D3",
  border = "white",
  xlab = "Biomarker concentration",
  ylab = "Frequency",
  main = "Distribution of biomarker values"
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_07_Tables_and_Frequency_Distributions_files/figure-gfm/biomarker-histogram-1.png" alt="Histogram of the simulated continuous biomarker values." width="85%" />
<p class="caption">

Histogram of the simulated continuous biomarker values.
</p>

</div>

## 12.1 Bar chart versus histogram

| Feature | Bar chart | Histogram |
|----|----|----|
| Data type | Categorical or discrete | Continuous numerical |
| Horizontal axis | Categories | Numerical intervals |
| Bar order | May be rearranged for nominal data | Must follow numerical order |
| Gaps | Usually present | Usually absent |
| Width meaning | Mostly visual | Represents interval width |
| Main purpose | Compare categories | Show distribution shape |

Do not use a histogram for genotype labels such as `AA`, `AG` and `GG`.
Do not use a categorical bar chart of every unique biomarker value when
the variable is continuous.

# 13. Frequency Polygon and Cumulative Distribution

A **frequency polygon** joins frequencies at class midpoints. It is
useful for comparing multiple distributions.

``` r
common_breaks <- pretty(range(clinical_data$biomarker), n = 8)

case_hist <- hist(
  clinical_data$biomarker[clinical_data$disease_status == "Case"],
  breaks = common_breaks,
  plot = FALSE
)

control_hist <- hist(
  clinical_data$biomarker[clinical_data$disease_status == "Control"],
  breaks = common_breaks,
  plot = FALSE
)

y_max <- max(case_hist$counts, control_hist$counts)

plot(case_hist$mids, case_hist$counts, type = "o", pch = 19,
     col = "#D95F02", ylim = c(0, y_max + 2),
     xlab = "Biomarker concentration", ylab = "Frequency",
     main = "Biomarker frequency polygons")
lines(control_hist$mids, control_hist$counts, type = "o", pch = 17,
      col = "#1B9E77")
legend("topright", legend = c("Case", "Control"),
       col = c("#D95F02", "#1B9E77"), pch = c(19, 17),
       lty = 1, bty = "n")
```

<div class="figure" style="text-align: center">

<img src="Chapter_07_Tables_and_Frequency_Distributions_files/figure-gfm/frequency-polygon-1.png" alt="Frequency polygons compare biomarker distributions between cases and controls." width="85%" />
<p class="caption">

Frequency polygons compare biomarker distributions between cases and
controls.
</p>

</div>

The two groups must use identical class boundaries for a fair
comparison.

## 13.1 Empirical cumulative distribution function

The empirical cumulative distribution function, or ECDF, gives the
proportion of observations less than or equal to each value.

``` r
plot(
  ecdf(clinical_data$biomarker[clinical_data$disease_status == "Case"]),
  col = "#D95F02", lwd = 2,
  xlab = "Biomarker concentration",
  ylab = "Cumulative proportion",
  main = "Empirical cumulative distributions"
)
lines(
  ecdf(clinical_data$biomarker[clinical_data$disease_status == "Control"]),
  col = "#1B9E77", lwd = 2
)
legend("bottomright", legend = c("Case", "Control"),
       col = c("#D95F02", "#1B9E77"), lwd = 2, bty = "n")
```

<div class="figure" style="text-align: center">

<img src="Chapter_07_Tables_and_Frequency_Distributions_files/figure-gfm/ecdf-plot-1.png" alt="Empirical cumulative distributions of biomarker values by disease status." width="85%" />
<p class="caption">

Empirical cumulative distributions of biomarker values by disease
status.
</p>

</div>

Unlike a histogram, an ECDF does not require choosing bins.

# 14. Two-Way Contingency Tables

A **contingency table**, or cross-tabulation, summarizes two categorical
variables together.

## 14.1 Disease status by recorded sex

``` r
sex_disease_table <- table(
  Recorded_sex = clinical_data$recorded_sex,
  Disease_status = clinical_data$disease_status
)

print_html_table(
  sex_disease_table,
  caption = "Disease status by recorded sex."
)
```

<table class="chapter-table">

<caption>

Disease status by recorded sex.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Recorded sex
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

31
</td>

<td style="text-align:right;">

36
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

20
</td>

<td style="text-align:right;">

33
</td>

</tr>

</tbody>

</table>

Each interior cell is a **joint frequency**. For example, the cell at
row `Female` and column `Case` counts participants who satisfy both
conditions.

## 14.2 Add marginal totals

``` r
print_html_table(
  addmargins(sex_disease_table),
  caption = "Disease status by recorded sex with marginal totals."
)
```

<table class="chapter-table">

<caption>

Disease status by recorded sex with marginal totals.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Recorded sex
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

<th style="text-align:right;">

Sum
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

31
</td>

<td style="text-align:right;">

36
</td>

<td style="text-align:right;">

67
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

20
</td>

<td style="text-align:right;">

33
</td>

<td style="text-align:right;">

53
</td>

</tr>

<tr>

<td style="text-align:left;">

Sum
</td>

<td style="text-align:right;">

51
</td>

<td style="text-align:right;">

69
</td>

<td style="text-align:right;">

120
</td>

</tr>

</tbody>

</table>

The final row contains column totals, the final column contains row
totals, and the bottom-right value is the grand total.

## 14.3 Create a contingency table with `xtabs()`

``` r
print_html_table(
  xtabs(~ recorded_sex + disease_status, data = clinical_data),
  caption = "Contingency table created with xtabs()."
)
```

<table class="chapter-table">

<caption>

Contingency table created with xtabs().
</caption>

<thead>

<tr>

<th style="text-align:left;">

recorded sex
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

31
</td>

<td style="text-align:right;">

36
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

20
</td>

<td style="text-align:right;">

33
</td>

</tr>

</tbody>

</table>

`xtabs()` is convenient because its formula syntax extends naturally to
more variables.

# 15. Joint, Row and Column Proportions

The denominator changes the scientific question.

## 15.1 Joint proportions

``` r
print_html_table(
  round(prop.table(sex_disease_table), 3),
  caption = "Joint proportions of recorded sex and disease status."
)
```

<table class="chapter-table">

<caption>

Joint proportions of recorded sex and disease status.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Recorded sex
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

0.258
</td>

<td style="text-align:right;">

0.300
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

0.167
</td>

<td style="text-align:right;">

0.275
</td>

</tr>

</tbody>

</table>

Every cell is divided by the grand total. All cells sum to 1.

Question answered:

> What proportion of all participants belongs to each sex–disease
> combination?

## 15.2 Row proportions

``` r
print_html_table(
  round(prop.table(sex_disease_table, margin = 1), 3),
  caption = "Disease-status proportions within recorded-sex groups."
)
```

<table class="chapter-table">

<caption>

Disease-status proportions within recorded-sex groups.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Recorded sex
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

0.463
</td>

<td style="text-align:right;">

0.537
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

0.377
</td>

<td style="text-align:right;">

0.623
</td>

</tr>

</tbody>

</table>

Every row sums to 1.

Question answered:

> Within each recorded-sex group, what proportion are cases and
> controls?

## 15.3 Column proportions

``` r
print_html_table(
  round(prop.table(sex_disease_table, margin = 2), 3),
  caption = "Recorded-sex proportions within disease-status groups."
)
```

<table class="chapter-table">

<caption>

Recorded-sex proportions within disease-status groups.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Recorded sex
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:right;">

0.608
</td>

<td style="text-align:right;">

0.522
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:right;">

0.392
</td>

<td style="text-align:right;">

0.478
</td>

</tr>

</tbody>

</table>

Every column sums to 1.

Question answered:

> Within cases or controls, what proportion belongs to each recorded-sex
> group?

> **Never report “the percentage” without specifying its denominator.**

# 16. Visualizing a Two-Way Table

A grouped bar chart can display a contingency table.

``` r
barplot(
  sex_disease_table,
  beside = TRUE,
  col = c("#7570B3", "#E7298A"),
  border = NA,
  xlab = "Disease status",
  ylab = "Number of participants",
  main = "Disease status by recorded sex"
)
legend(
  "topright",
  legend = rownames(sex_disease_table),
  fill = c("#7570B3", "#E7298A"),
  bty = "n"
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_07_Tables_and_Frequency_Distributions_files/figure-gfm/grouped-bar-chart-1.png" alt="Disease-status counts within recorded-sex groups." width="85%" />
<p class="caption">

Disease-status counts within recorded-sex groups.
</p>

</div>

For comparing group composition when group sizes differ, a 100% stacked
bar chart may be more informative.

``` r
column_percent <- 100 * prop.table(sex_disease_table, margin = 2)

barplot(
  column_percent,
  col = c("#7570B3", "#E7298A"),
  border = NA,
  xlab = "Disease status",
  ylab = "Percentage within disease-status group",
  main = "Composition of cases and controls",
  ylim = c(0, 100)
)
legend(
  "topright",
  legend = rownames(column_percent),
  fill = c("#7570B3", "#E7298A"),
  bty = "n"
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_07_Tables_and_Frequency_Distributions_files/figure-gfm/proportional-stacked-bar-1.png" alt="Each disease-status column sums to 100%." width="85%" />
<p class="caption">

Each disease-status column sums to 100%.
</p>

</div>

The 100% chart shows composition but hides the difference in group
sample sizes. Counts and percentages serve different purposes.

# 17. Three-Way and Multi-Way Tables

More than two categorical variables can be summarized together.

``` r
three_way <- xtabs(
  ~ recorded_sex + disease_status + qc_status,
  data = clinical_data
)

print_html_table(
  three_way,
  caption = "Three-way frequencies by recorded sex, disease status and QC status."
)
```

<table class="chapter-table">

<caption>

Three-way frequencies by recorded sex, disease status and QC status.
</caption>

<thead>

<tr>

<th style="text-align:left;">

recorded sex
</th>

<th style="text-align:left;">

disease status
</th>

<th style="text-align:left;">

qc status
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Fail
</td>

<td style="text-align:right;">

2
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Fail
</td>

<td style="text-align:right;">

1
</td>

</tr>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Fail
</td>

<td style="text-align:right;">

0
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Fail
</td>

<td style="text-align:right;">

6
</td>

</tr>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

29
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

19
</td>

</tr>

<tr>

<td style="text-align:left;">

Female
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

36
</td>

</tr>

<tr>

<td style="text-align:left;">

Male
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

27
</td>

</tr>

</tbody>

</table>

The result is a three-dimensional array. `ftable()` displays it in a
flatter layout.

``` r
print_html_table(
  ftable(three_way),
  caption = "Flattened three-way contingency table."
)
```

<table class="chapter-table">

<caption>

Flattened three-way contingency table.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Fail
</th>

<th style="text-align:right;">

Pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Female_Case
</td>

<td style="text-align:right;">

2
</td>

<td style="text-align:right;">

29
</td>

</tr>

<tr>

<td style="text-align:left;">

Female_Control
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

36
</td>

</tr>

<tr>

<td style="text-align:left;">

Male_Case
</td>

<td style="text-align:right;">

1
</td>

<td style="text-align:right;">

19
</td>

</tr>

<tr>

<td style="text-align:left;">

Male_Control
</td>

<td style="text-align:right;">

6
</td>

<td style="text-align:right;">

27
</td>

</tr>

</tbody>

</table>

Multi-way tables can become difficult to read, especially when many
cells are empty. Use them to answer a defined question rather than
displaying every possible combination.

# 18. Counts, Proportions, Percentages, Ratios and Rates

These terms are related but not interchangeable.

| Measure | Meaning | Example |
|----|----|----|
| Count | Number of observed events or units | 24 infections |
| Proportion | Numerator is part of denominator | 24 infected among 200 participants = 0.12 |
| Percentage | Proportion multiplied by 100 | 12% infected |
| Ratio | Numerator need not be part of denominator | 24 infected : 176 uninfected |
| Rate | Occurrence per amount of time at risk | 8 infections per 1,000 person-months |

## 18.1 Example calculations

``` r
infected <- 24
participants <- 200
person_months <- 3000

proportion_infected <- infected / participants
percentage_infected <- 100 * proportion_infected
incidence_rate <- infected / person_months * 1000

print_html_table(data.frame(
  Measure = c("Count", "Proportion", "Percentage",
              "Rate per 1,000 person-months"),
  Value = c(infected, proportion_infected,
            percentage_infected, incidence_rate)
), caption = "Count, proportion, percentage and incidence rate.")
```

<table class="chapter-table">

<caption>

Count, proportion, percentage and incidence rate.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Measure
</th>

<th style="text-align:right;">

Value
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Count
</td>

<td style="text-align:right;">

24.00
</td>

</tr>

<tr>

<td style="text-align:left;">

Proportion
</td>

<td style="text-align:right;">

0.12
</td>

</tr>

<tr>

<td style="text-align:left;">

Percentage
</td>

<td style="text-align:right;">

12.00
</td>

</tr>

<tr>

<td style="text-align:left;">

Rate per 1,000 person-months
</td>

<td style="text-align:right;">

8.00
</td>

</tr>

</tbody>

</table>

A rate requires a time component or person-time denominator. The
percentage of participants who already have a disease is a prevalence
proportion, not an incidence rate.

# 19. Genotype and Allele Frequency Tables

Genetic data provide an important biological application of frequency
tables.

Suppose a biallelic locus has alleles `A` and `G`, producing genotypes
`AA`, `AG` and `GG`.

## 19.1 Genotype frequencies

``` r
genotype_counts <- table(clinical_data$genotype, useNA = "ifany")
print_html_table(
  genotype_counts,
  caption = "Genotype counts including missing observations."
)
```

<table class="chapter-table">

<caption>

Genotype counts including missing observations.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

AA
</td>

<td style="text-align:right;">

59
</td>

</tr>

<tr>

<td style="text-align:left;">

AG
</td>

<td style="text-align:right;">

49
</td>

</tr>

<tr>

<td style="text-align:left;">

GG
</td>

<td style="text-align:right;">

9
</td>

</tr>

<tr>

<td style="text-align:left;">

NA
</td>

<td style="text-align:right;">

3
</td>

</tr>

</tbody>

</table>

For genotype-frequency calculations, missing genotypes should be
excluded from the denominator but reported separately.

``` r
called_genotypes <- clinical_data$genotype[!is.na(clinical_data$genotype)]
called_counts <- table(factor(called_genotypes,
                              levels = c("AA", "AG", "GG")))

genotype_distribution <- data.frame(
  Genotype = names(called_counts),
  Count = as.vector(called_counts),
  Frequency = round(as.vector(prop.table(called_counts)), 3),
  stringsAsFactors = FALSE
)

print_html_table(
  genotype_distribution,
  caption = "Genotype counts and frequencies among called genotypes."
)
```

<table class="chapter-table">

<caption>

Genotype counts and frequencies among called genotypes.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Genotype
</th>

<th style="text-align:right;">

Count
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

AA
</td>

<td style="text-align:right;">

59
</td>

<td style="text-align:right;">

0.504
</td>

</tr>

<tr>

<td style="text-align:left;">

AG
</td>

<td style="text-align:right;">

49
</td>

<td style="text-align:right;">

0.419
</td>

</tr>

<tr>

<td style="text-align:left;">

GG
</td>

<td style="text-align:right;">

9
</td>

<td style="text-align:right;">

0.077
</td>

</tr>

</tbody>

</table>

## 19.2 Allele counts

Every successfully genotyped diploid individual contributes two alleles.

If $n_{AA}$, $n_{AG}$ and $n_{GG}$ are genotype counts:

$$n_A = 2n_{AA} + n_{AG}$$

$$n_G = 2n_{GG} + n_{AG}.$$

``` r
n_AA <- unname(called_counts["AA"])
n_AG <- unname(called_counts["AG"])
n_GG <- unname(called_counts["GG"])

A_count <- 2 * n_AA + n_AG
G_count <- 2 * n_GG + n_AG
total_alleles <- A_count + G_count

allele_distribution <- data.frame(
  Allele = c("A", "G"),
  Count = c(A_count, G_count),
  Frequency = round(c(A_count, G_count) / total_alleles, 3),
  stringsAsFactors = FALSE
)

print_html_table(
  allele_distribution,
  caption = "Allele counts and frequencies."
)
```

<table class="chapter-table">

<caption>

Allele counts and frequencies.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Allele
</th>

<th style="text-align:right;">

Count
</th>

<th style="text-align:right;">

Frequency
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

A
</td>

<td style="text-align:right;">

167
</td>

<td style="text-align:right;">

0.714
</td>

</tr>

<tr>

<td style="text-align:left;">

G
</td>

<td style="text-align:right;">

67
</td>

<td style="text-align:right;">

0.286
</td>

</tr>

</tbody>

</table>

The two allele frequencies should sum to 1, apart from display rounding.

``` r
sum(allele_distribution$Count / total_alleles)
```

    ## [1] 1

## 19.3 Genotype by disease status

``` r
genotype_disease <- table(
  Genotype = factor(clinical_data$genotype,
                    levels = c("AA", "AG", "GG")),
  Disease_status = clinical_data$disease_status,
  useNA = "no"
)

print_html_table(
  genotype_disease,
  caption = "Genotype counts by disease status."
)
```

<table class="chapter-table">

<caption>

Genotype counts by disease status.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Genotype
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

AA
</td>

<td style="text-align:right;">

21
</td>

<td style="text-align:right;">

38
</td>

</tr>

<tr>

<td style="text-align:left;">

AG
</td>

<td style="text-align:right;">

25
</td>

<td style="text-align:right;">

24
</td>

</tr>

<tr>

<td style="text-align:left;">

GG
</td>

<td style="text-align:right;">

4
</td>

<td style="text-align:right;">

5
</td>

</tr>

</tbody>

</table>

``` r
print_html_table(
  round(100 * prop.table(genotype_disease, margin = 2), 1),
  caption = "Genotype percentages within disease-status groups."
)
```

<table class="chapter-table">

<caption>

Genotype percentages within disease-status groups.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Genotype
</th>

<th style="text-align:right;">

Case
</th>

<th style="text-align:right;">

Control
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

AA
</td>

<td style="text-align:right;">

42
</td>

<td style="text-align:right;">

56.7
</td>

</tr>

<tr>

<td style="text-align:left;">

AG
</td>

<td style="text-align:right;">

50
</td>

<td style="text-align:right;">

35.8
</td>

</tr>

<tr>

<td style="text-align:left;">

GG
</td>

<td style="text-align:right;">

8
</td>

<td style="text-align:right;">

7.5
</td>

</tr>

</tbody>

</table>

These descriptive differences do not establish genetic association.
Later chapters will introduce chi-squared tests, Fisher’s exact test,
logistic regression, Hardy–Weinberg equilibrium and adjustment for
population structure.

# 20. Bioinformatics Count Tables

The word **count** has different roles in bioinformatics.

## 20.1 RNA-seq count matrix

In an RNA-seq count matrix:

- rows commonly represent genes;
- columns represent biological samples; and
- cells contain reads or fragments assigned to a gene.

``` r
set.seed(789)

rna_counts <- matrix(
  rpois(30, lambda = 40),
  nrow = 6,
  dimnames = list(
    paste0("Gene_", LETTERS[1:6]),
    paste0("Sample_", 1:5)
  )
)

print_html_table(
  rna_counts,
  caption = "Simulated RNA-seq count matrix."
)
```

<table class="chapter-table">

<caption>

Simulated RNA-seq count matrix.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Sample 1
</th>

<th style="text-align:right;">

Sample 2
</th>

<th style="text-align:right;">

Sample 3
</th>

<th style="text-align:right;">

Sample 4
</th>

<th style="text-align:right;">

Sample 5
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Gene_A
</td>

<td style="text-align:right;">

43
</td>

<td style="text-align:right;">

44
</td>

<td style="text-align:right;">

36
</td>

<td style="text-align:right;">

28
</td>

<td style="text-align:right;">

44
</td>

</tr>

<tr>

<td style="text-align:left;">

Gene_B
</td>

<td style="text-align:right;">

25
</td>

<td style="text-align:right;">

37
</td>

<td style="text-align:right;">

36
</td>

<td style="text-align:right;">

38
</td>

<td style="text-align:right;">

44
</td>

</tr>

<tr>

<td style="text-align:left;">

Gene_C
</td>

<td style="text-align:right;">

44
</td>

<td style="text-align:right;">

36
</td>

<td style="text-align:right;">

35
</td>

<td style="text-align:right;">

45
</td>

<td style="text-align:right;">

36
</td>

</tr>

<tr>

<td style="text-align:left;">

Gene_D
</td>

<td style="text-align:right;">

36
</td>

<td style="text-align:right;">

36
</td>

<td style="text-align:right;">

58
</td>

<td style="text-align:right;">

38
</td>

<td style="text-align:right;">

31
</td>

</tr>

<tr>

<td style="text-align:left;">

Gene_E
</td>

<td style="text-align:right;">

39
</td>

<td style="text-align:right;">

40
</td>

<td style="text-align:right;">

33
</td>

<td style="text-align:right;">

37
</td>

<td style="text-align:right;">

38
</td>

</tr>

<tr>

<td style="text-align:left;">

Gene_F
</td>

<td style="text-align:right;">

26
</td>

<td style="text-align:right;">

36
</td>

<td style="text-align:right;">

30
</td>

<td style="text-align:right;">

42
</td>

<td style="text-align:right;">

40
</td>

</tr>

</tbody>

</table>

This matrix is not a one-way frequency table of participants. Each entry
is a molecular count produced through a sequencing process. Library
size, gene length, composition and biological variability affect
interpretation.

``` r
print_html_table(data.frame(
  Sample = colnames(rna_counts),
  Total_assigned_reads = colSums(rna_counts),
  stringsAsFactors = FALSE
), caption = "Total assigned RNA-seq reads by sample.")
```

<table class="chapter-table">

<caption>

Total assigned RNA-seq reads by sample.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Sample
</th>

<th style="text-align:right;">

Total assigned reads
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Sample_1
</td>

<td style="text-align:right;">

213
</td>

</tr>

<tr>

<td style="text-align:left;">

Sample_2
</td>

<td style="text-align:right;">

229
</td>

</tr>

<tr>

<td style="text-align:left;">

Sample_3
</td>

<td style="text-align:right;">

228
</td>

</tr>

<tr>

<td style="text-align:left;">

Sample_4
</td>

<td style="text-align:right;">

228
</td>

</tr>

<tr>

<td style="text-align:left;">

Sample_5
</td>

<td style="text-align:right;">

233
</td>

</tr>

</tbody>

</table>

Raw RNA-seq counts should not normally be converted to percentages and
compared naively across samples for differential-expression inference.
Specialized models and normalization are needed.

## 20.2 Variant consequence counts

A simple frequency table is appropriate for summarizing annotated
variant consequences.

``` r
set.seed(987)

variant_consequence <- sample(
  c("Intronic", "Missense", "Synonymous", "Intergenic", "Stop gained"),
  size = 500,
  replace = TRUE,
  prob = c(0.44, 0.15, 0.12, 0.27, 0.02)
)

consequence_counts <- sort(table(variant_consequence), decreasing = TRUE)

consequence_distribution <- data.frame(
  Consequence = names(consequence_counts),
  Count = as.vector(consequence_counts),
  Percentage = round(100 * as.vector(prop.table(consequence_counts)), 1),
  stringsAsFactors = FALSE
)

print_html_table(
  consequence_distribution,
  caption = "Annotated variant-consequence frequencies."
)
```

<table class="chapter-table">

<caption>

Annotated variant-consequence frequencies.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Consequence
</th>

<th style="text-align:right;">

Count
</th>

<th style="text-align:right;">

Percentage
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Intronic
</td>

<td style="text-align:right;">

219
</td>

<td style="text-align:right;">

43.8
</td>

</tr>

<tr>

<td style="text-align:left;">

Intergenic
</td>

<td style="text-align:right;">

139
</td>

<td style="text-align:right;">

27.8
</td>

</tr>

<tr>

<td style="text-align:left;">

Missense
</td>

<td style="text-align:right;">

68
</td>

<td style="text-align:right;">

13.6
</td>

</tr>

<tr>

<td style="text-align:left;">

Synonymous
</td>

<td style="text-align:right;">

67
</td>

<td style="text-align:right;">

13.4
</td>

</tr>

<tr>

<td style="text-align:left;">

Stop gained
</td>

<td style="text-align:right;">

7
</td>

<td style="text-align:right;">

1.4
</td>

</tr>

</tbody>

</table>

Counts depend on the annotation rules. A single variant can have
multiple transcript consequences, so specify whether you counted
variants, transcripts or one selected consequence per variant.

# 21. Zero Counts, Sparse Tables and Small Numbers

A **zero cell** means no observations occurred in a category
combination. It may reflect:

- a truly impossible combination;
- a rare event;
- inadequate sample size;
- a category definition problem; or
- missing or filtered observations.

A table is **sparse** when many cells contain small or zero counts.

Sparse tables create problems for some statistical methods. Combining
categories may help only when the combination is scientifically
defensible. Never merge distinct biological categories solely to obtain
a preferred statistical result.

Small counts can also threaten participant privacy. Public reports may
need suppression or aggregation according to institutional and legal
rules.

# 22. Creating a Clean Summary Table

A useful descriptive table reports a count and percentage together.

``` r
frequency_table <- function(x, include_missing = TRUE, digits = 1) {
  use_na <- if (include_missing) "ifany" else "no"
  counts <- table(x, useNA = use_na)
  total <- sum(counts)

  result <- data.frame(
    Category = names(counts),
    N = as.vector(counts),
    Percent = round(100 * as.vector(counts) / total, digits),
    stringsAsFactors = FALSE
  )

  result
}

print_html_table(
  frequency_table(clinical_data$qc_status),
  caption = "QC-status counts and percentages."
)
```

<table class="chapter-table">

<caption>

QC-status counts and percentages.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

N
</th>

<th style="text-align:right;">

Percent
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Fail
</td>

<td style="text-align:right;">

9
</td>

<td style="text-align:right;">

7.5
</td>

</tr>

<tr>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

111
</td>

<td style="text-align:right;">

92.5
</td>

</tr>

</tbody>

</table>

The function:

1.  receives a vector `x`;
2.  decides whether to include missing values;
3.  counts categories with `table()`;
4.  calculates percentages using the displayed total; and
5.  returns a regular data frame that is safe to display with
    `print_html_table()`.

## 22.1 Add a display column

``` r
qc_summary <- frequency_table(clinical_data$qc_status)

qc_summary$Display <- paste0(
  qc_summary$N,
  " (",
  format(qc_summary$Percent, nsmall = 1),
  "%)"
)

print_html_table(
  qc_summary,
  caption = "QC-status summary with an n-percent display column."
)
```

<table class="chapter-table">

<caption>

QC-status summary with an n-percent display column.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

N
</th>

<th style="text-align:right;">

Percent
</th>

<th style="text-align:left;">

Display
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Fail
</td>

<td style="text-align:right;">

9
</td>

<td style="text-align:right;">

7.5
</td>

<td style="text-align:left;">

9 ( 7.5%)
</td>

</tr>

<tr>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

111
</td>

<td style="text-align:right;">

92.5
</td>

<td style="text-align:left;">

111 (92.5%)
</td>

</tr>

</tbody>

</table>

Keep numerical count and percentage columns in the analysis dataset. The
combined display column is mainly for a report.

# 23. An Introductory “Table 1”

Clinical and epidemiological reports often begin with a table describing
the sample. It is commonly called **Table 1**.

At this stage, we can create a simple version containing categorical
frequencies and broad numerical summaries. Measures of central tendency
and dispersion will be covered in the next chapters.

``` r
case_data <- clinical_data[clinical_data$disease_status == "Case", ]
control_data <- clinical_data[clinical_data$disease_status == "Control", ]

table_one <- data.frame(
  Characteristic = c(
    "Participants, n",
    "Female, n (%)",
    "QC pass, n (%)",
    "Age, mean",
    "Biomarker, mean"
  ),
  Control = c(
    nrow(control_data),
    sprintf("%d (%.1f%%)",
            sum(control_data$recorded_sex == "Female"),
            100 * mean(control_data$recorded_sex == "Female")),
    sprintf("%d (%.1f%%)",
            sum(control_data$qc_status == "Pass"),
            100 * mean(control_data$qc_status == "Pass")),
    sprintf("%.1f", mean(control_data$age_years)),
    sprintf("%.2f", mean(control_data$biomarker))
  ),
  Case = c(
    nrow(case_data),
    sprintf("%d (%.1f%%)",
            sum(case_data$recorded_sex == "Female"),
            100 * mean(case_data$recorded_sex == "Female")),
    sprintf("%d (%.1f%%)",
            sum(case_data$qc_status == "Pass"),
            100 * mean(case_data$qc_status == "Pass")),
    sprintf("%.1f", mean(case_data$age_years)),
    sprintf("%.2f", mean(case_data$biomarker))
  ),
  stringsAsFactors = FALSE,
  check.names = FALSE
)

print_html_table(
  table_one,
  caption = "Introductory descriptive Table 1 by disease status."
)
```

<table class="chapter-table">

<caption>

Introductory descriptive Table 1 by disease status.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Characteristic
</th>

<th style="text-align:left;">

Control
</th>

<th style="text-align:left;">

Case
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Participants, n
</td>

<td style="text-align:left;">

69
</td>

<td style="text-align:left;">

51
</td>

</tr>

<tr>

<td style="text-align:left;">

Female, n (%)
</td>

<td style="text-align:left;">

36 (52.2%)
</td>

<td style="text-align:left;">

31 (60.8%)
</td>

</tr>

<tr>

<td style="text-align:left;">

QC pass, n (%)
</td>

<td style="text-align:left;">

63 (91.3%)
</td>

<td style="text-align:left;">

48 (94.1%)
</td>

</tr>

<tr>

<td style="text-align:left;">

Age, mean
</td>

<td style="text-align:left;">

50.1
</td>

<td style="text-align:left;">

51.4
</td>

</tr>

<tr>

<td style="text-align:left;">

Biomarker, mean
</td>

<td style="text-align:left;">

4.76
</td>

<td style="text-align:left;">

6.07
</td>

</tr>

</tbody>

</table>

Table 1 is descriptive. It should help readers understand who was
studied. Automatic hypothesis tests in every Table 1 row are often
unhelpful, particularly in randomized trials where any baseline
differences arose by chance.

# 24. Integrated Case Study: Sequencing Quality-Control Summary

## 24.1 Scientific setting

A laboratory sequenced 240 samples across two disease groups, three
centres and four batches. We want to describe QC outcomes before
downstream analysis.

## 24.2 Simulate the sample-level data

``` r
set.seed(246)

qc_data <- data.frame(
  sample_id = sprintf("SEQ%03d", 1:240),
  centre = sample(c("Centre_A", "Centre_B", "Centre_C"),
                  240, replace = TRUE, prob = c(0.40, 0.35, 0.25)),
  disease_group = sample(c("Control", "Case"),
                         240, replace = TRUE),
  batch = sample(paste0("Batch_", 1:4),
                 240, replace = TRUE),
  stringsAsFactors = FALSE
)

# Make failure slightly more common in Centre_C for demonstration
failure_probability <- ifelse(qc_data$centre == "Centre_C", 0.18, 0.07)
qc_data$qc_result <- ifelse(
  rbinom(240, size = 1, prob = failure_probability) == 1,
  "Fail", "Pass"
)

print_html_table(
  head(qc_data),
  caption = "First six samples in the sequencing QC case study."
)
```

<table class="chapter-table">

<caption>

First six samples in the sequencing QC case study.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

centre
</th>

<th style="text-align:left;">

disease group
</th>

<th style="text-align:left;">

batch
</th>

<th style="text-align:left;">

qc result
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

SEQ001
</td>

<td style="text-align:left;">

Centre_B
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Batch_3
</td>

<td style="text-align:left;">

Pass
</td>

</tr>

<tr>

<td style="text-align:left;">

SEQ002
</td>

<td style="text-align:left;">

Centre_A
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Batch_4
</td>

<td style="text-align:left;">

Pass
</td>

</tr>

<tr>

<td style="text-align:left;">

SEQ003
</td>

<td style="text-align:left;">

Centre_B
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Batch_1
</td>

<td style="text-align:left;">

Pass
</td>

</tr>

<tr>

<td style="text-align:left;">

SEQ004
</td>

<td style="text-align:left;">

Centre_A
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Batch_2
</td>

<td style="text-align:left;">

Pass
</td>

</tr>

<tr>

<td style="text-align:left;">

SEQ005
</td>

<td style="text-align:left;">

Centre_A
</td>

<td style="text-align:left;">

Case
</td>

<td style="text-align:left;">

Batch_2
</td>

<td style="text-align:left;">

Pass
</td>

</tr>

<tr>

<td style="text-align:left;">

SEQ006
</td>

<td style="text-align:left;">

Centre_B
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:left;">

Batch_2
</td>

<td style="text-align:left;">

Pass
</td>

</tr>

</tbody>

</table>

## 24.3 Overall QC frequency

``` r
overall_qc <- frequency_table(qc_data$qc_result)
print_html_table(
  overall_qc,
  caption = "Overall sequencing QC frequencies."
)
```

<table class="chapter-table">

<caption>

Overall sequencing QC frequencies.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

N
</th>

<th style="text-align:right;">

Percent
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Fail
</td>

<td style="text-align:right;">

31
</td>

<td style="text-align:right;">

12.9
</td>

</tr>

<tr>

<td style="text-align:left;">

Pass
</td>

<td style="text-align:right;">

209
</td>

<td style="text-align:right;">

87.1
</td>

</tr>

</tbody>

</table>

## 24.4 QC by centre

``` r
qc_by_centre <- table(
  Centre = qc_data$centre,
  QC_result = qc_data$qc_result
)

print_html_table(
  qc_by_centre,
  caption = "Sequencing QC counts by centre."
)
```

<table class="chapter-table">

<caption>

Sequencing QC counts by centre.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Centre
</th>

<th style="text-align:right;">

Fail
</th>

<th style="text-align:right;">

Pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Centre_A
</td>

<td style="text-align:right;">

13
</td>

<td style="text-align:right;">

99
</td>

</tr>

<tr>

<td style="text-align:left;">

Centre_B
</td>

<td style="text-align:right;">

11
</td>

<td style="text-align:right;">

71
</td>

</tr>

<tr>

<td style="text-align:left;">

Centre_C
</td>

<td style="text-align:right;">

7
</td>

<td style="text-align:right;">

39
</td>

</tr>

</tbody>

</table>

``` r
print_html_table(
  round(100 * prop.table(qc_by_centre, margin = 1), 1),
  caption = "Sequencing QC percentages within centres."
)
```

<table class="chapter-table">

<caption>

Sequencing QC percentages within centres.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Centre
</th>

<th style="text-align:right;">

Fail
</th>

<th style="text-align:right;">

Pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Centre_A
</td>

<td style="text-align:right;">

11.6
</td>

<td style="text-align:right;">

88.4
</td>

</tr>

<tr>

<td style="text-align:left;">

Centre_B
</td>

<td style="text-align:right;">

13.4
</td>

<td style="text-align:right;">

86.6
</td>

</tr>

<tr>

<td style="text-align:left;">

Centre_C
</td>

<td style="text-align:right;">

15.2
</td>

<td style="text-align:right;">

84.8
</td>

</tr>

</tbody>

</table>

Row percentages are appropriate because the question is:

> Within each centre, what percentage of samples passed or failed?

## 24.5 QC by disease group and batch

``` r
qc_three_way <- xtabs(
  ~ disease_group + batch + qc_result,
  data = qc_data
)

print_html_table(
  ftable(qc_three_way),
  caption = "QC outcome by disease group and sequencing batch."
)
```

<table class="chapter-table">

<caption>

QC outcome by disease group and sequencing batch.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Fail
</th>

<th style="text-align:right;">

Pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Case_Batch_1
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

29
</td>

</tr>

<tr>

<td style="text-align:left;">

Case_Batch_2
</td>

<td style="text-align:right;">

8
</td>

<td style="text-align:right;">

28
</td>

</tr>

<tr>

<td style="text-align:left;">

Case_Batch_3
</td>

<td style="text-align:right;">

6
</td>

<td style="text-align:right;">

21
</td>

</tr>

<tr>

<td style="text-align:left;">

Case_Batch_4
</td>

<td style="text-align:right;">

3
</td>

<td style="text-align:right;">

21
</td>

</tr>

<tr>

<td style="text-align:left;">

Control_Batch_1
</td>

<td style="text-align:right;">

5
</td>

<td style="text-align:right;">

26
</td>

</tr>

<tr>

<td style="text-align:left;">

Control_Batch_2
</td>

<td style="text-align:right;">

5
</td>

<td style="text-align:right;">

30
</td>

</tr>

<tr>

<td style="text-align:left;">

Control_Batch_3
</td>

<td style="text-align:right;">

2
</td>

<td style="text-align:right;">

23
</td>

</tr>

<tr>

<td style="text-align:left;">

Control_Batch_4
</td>

<td style="text-align:right;">

2
</td>

<td style="text-align:right;">

31
</td>

</tr>

</tbody>

</table>

## 24.6 Plot centre-specific failure percentages

``` r
centre_percent <- 100 * prop.table(qc_by_centre, margin = 1)
failure_percent <- centre_percent[, "Fail"]

barplot(
  failure_percent,
  col = c("#1B9E77", "#7570B3", "#D95F02"),
  border = NA,
  ylab = "QC failure percentage",
  xlab = "Sequencing centre",
  main = "QC failure varies across centres",
  ylim = c(0, max(failure_percent) * 1.25)
)
abline(h = mean(qc_data$qc_result == "Fail") * 100,
       lty = 2, lwd = 2, col = "grey35")
```

<div class="figure" style="text-align: center">

<img src="Chapter_07_Tables_and_Frequency_Distributions_files/figure-gfm/qc-case-study-plot-1.png" alt="Simulated sequencing QC failure percentage by centre." width="85%" />
<p class="caption">

Simulated sequencing QC failure percentage by centre.
</p>

</div>

This descriptive difference is a signal to investigate. It does not by
itself prove that the centre caused the failures. Sample type, storage,
extraction method or batch allocation might differ between centres.

# 25. Common Mistakes

## Mistake 1: Reporting percentages without counts

“50% failed” could mean 1 of 2 samples or 500 of 1,000. Report both
count and denominator.

## Mistake 2: Ignoring missing values

Default functions may exclude missing values. State whether percentages
use all observations or only non-missing observations.

## Mistake 3: Using the wrong denominator

Row, column and total percentages answer different questions.

## Mistake 4: Treating ordinal categories as nominal

Preserve the biological order of categories such as low, medium and
high.

## Mistake 5: Using overlapping intervals

Age groups “20–30” and “30–40” both appear to contain age 30. Define
boundaries precisely.

## Mistake 6: Choosing bins to create a desired visual impression

Show reasonable alternative widths during exploration. Do not manipulate
bins to exaggerate or hide distribution features.

## Mistake 7: Confusing a bar chart with a histogram

Bar charts summarize categories; histograms summarize numerical
intervals.

## Mistake 8: Treating transcript counts as variant counts

Define exactly what each row or count represents.

## Mistake 9: Interpreting descriptive differences as proof

A frequency table describes the sample. Statistical inference and causal
interpretation require additional design and analysis.

## Mistake 10: Calculating prevalence from a case-control sample

The case-to-control ratio was often fixed by design and does not
estimate population prevalence.

# 26. Practical Reporting Checklist

Before presenting a table, ask:

- What is the observational unit?
- What does one count represent?
- Is the variable nominal, ordinal, discrete or continuous?
- Is the category order meaningful?
- Are all expected categories shown?
- Are missing values visible or explicitly excluded?
- What is the denominator for every percentage?
- Do percentages sum to approximately 100%, allowing for rounding?
- Are class intervals non-overlapping and clearly labelled?
- Are counts so small that privacy or sparse-data problems arise?
- Does the title state the population, variable and relevant time or
  setting?
- Can another researcher reproduce the table from the code?

# 27. Chapter Summary

- Frequency is the number of times a value or category occurs.
- Relative frequency divides a category count by a stated total.
- Percentage is relative frequency multiplied by 100.
- Cumulative frequency is appropriate only for ordered variables.
- `table()` creates frequency and contingency tables in base R.
- `prop.table()` calculates total, row or column proportions.
- `addmargins()` adds totals, while `xtabs()` uses formula notation.
- Factors preserve category order and can show defined zero-count
  categories.
- Missing values must be handled explicitly because they affect
  denominators.
- `cut()` converts continuous values into non-overlapping class
  intervals.
- Bar charts display categories; histograms display continuous
  distributions.
- Counts, proportions, ratios and rates have different meanings.
- Genotype counts can be converted into allele counts for diploid
  samples.
- Omics count matrices require interpretation according to their
  biological and technical units.
- A descriptive table organizes evidence but does not itself establish
  association or causation.

# 28. Check Your Understanding

1.  What is the difference between frequency and relative frequency?
2.  Why should a percentage usually be accompanied by a count?
3.  When is cumulative frequency scientifically meaningful?
4.  How does `table(x, useNA = "ifany")` differ from `table(x)`?
5.  Why would you convert `Low`, `Medium` and `High` to an ordered
    factor?
6.  What does `right = FALSE` mean in `cut()`?
7.  How does a histogram differ from a bar chart?
8.  What question is answered by row percentages in a contingency table?
9.  Why may column percentages answer a different question?
10. What is the difference between a proportion and a rate?
11. How many alleles are contributed by 50 successfully genotyped
    diploid individuals?
12. Why might a variant consequence count depend on transcript
    annotation rules?
13. What could produce a zero cell in a two-way table?
14. Why should frequency-polygon groups use the same class boundaries?
15. Can a QC table prove that a sequencing centre caused failures?
    Explain.

# 29. R Exercises

## Exercise 1: One-way table

Create a vector of 30 blood groups containing `A`, `B`, `AB` and `O`.
Produce counts, proportions and percentages.

## Exercise 2: Ordered categories

Create an ordered factor with the categories `Mild`, `Moderate` and
`Severe`. Build a cumulative frequency table.

## Exercise 3: Missingness

Add five `NA` values to a genotype vector. Compare the results of
`table()` using `useNA = "no"`, `"ifany"` and `"always"`.

## Exercise 4: Grouped ages

Simulate 200 ages. Create clinically meaningful age groups with `cut()`
and report frequency, percentage and cumulative percentage.

## Exercise 5: Histogram bins

Plot the same biomarker data using 5, 10 and 30 breaks and then the
Freedman–Diaconis rule. Explain how binning changes the visual
impression.

## Exercise 6: Two-way table

Create a treatment-by-response table. Calculate joint, row and column
proportions and explain each denominator.

## Exercise 7: Genotype frequencies

For genotype counts `AA = 40`, `AG = 45` and `GG = 15`, calculate
genotype and allele frequencies in R.

## Exercise 8: Variant annotation

Simulate 1,000 variant consequences. Produce a descending table
containing counts and percentages and display it with a bar chart.

## Exercise 9: QC summary function

Modify `frequency_table()` so it adds a final total row without
converting numeric columns to character.

## Exercise 10: Sparse table

Create a 4-by-4 contingency table containing several zero cells.
Identify scientifically defensible and indefensible ways to combine
categories.

# 30. Mini-Project: Pathogen Genomic Surveillance Summary

Create or simulate a sample-level dataset containing at least 500
pathogen genomes with:

- genome ID;
- region;
- collection year;
- host species;
- lineage;
- sequencing platform;
- QC status; and
- at least one variable containing missing values.

Your report should:

1.  define what one row represents;
2.  describe the denominator used in every table;
3.  create one-way frequency tables for region, lineage and QC status;
4.  display missingness counts and percentages;
5.  create collection-year groups if appropriate;
6.  calculate lineage proportions within each region;
7.  calculate QC-failure percentages within each sequencing platform;
8.  create one grouped bar chart and one 100% stacked bar chart;
9.  identify sparse or zero cells;
10. discuss whether database frequencies represent pathogen prevalence;
    and
11. provide reproducible R code and a brief scientific interpretation.

# 31. Glossary

| Term | Plain-language definition |
|----|----|
| Frequency | Number of observations in a value or category |
| Relative frequency | Category frequency divided by the total |
| Percentage | Relative frequency multiplied by 100 |
| Cumulative frequency | Running total across ordered values or classes |
| Frequency distribution | Summary showing how observations are distributed |
| Class interval | Numerical range used to group continuous values |
| Class width | Distance between interval boundaries |
| Contingency table | Table of joint frequencies for categorical variables |
| Joint frequency | Count satisfying a combination of categories |
| Marginal total | Row or column total in a contingency table |
| Row proportion | Cell count divided by its row total |
| Column proportion | Cell count divided by its column total |
| Factor | R data type representing defined categorical levels |
| Histogram | Adjacent-bin display of a numerical distribution |
| Bar chart | Separated-bar display of categorical frequencies |
| ECDF | Proportion of observations less than or equal to each value |
| Proportion | Fraction whose numerator is part of its denominator |
| Ratio | Comparison of two quantities without requiring part-to-whole structure |
| Rate | Event occurrence relative to time at risk |
| Sparse table | Table containing many small or zero cell counts |
| Denominator | Total quantity used to calculate a fraction or rate |

# 32. References

1.  Altman, D. G. (1991). *Practical Statistics for Medical Research*.
    Chapman and Hall.

2.  Kirkwood, B. R., & Sterne, J. A. C. (2003). *Essential Medical
    Statistics* (2nd ed.). Blackwell Science.

3.  Rosner, B. (2016). *Fundamentals of Biostatistics* (8th ed.).
    Cengage Learning.

4.  Agresti, A. (2019). *An Introduction to Categorical Data Analysis*
    (3rd ed.). Wiley.

5.  Freedman, D., & Diaconis, P. (1981). On the histogram as a density
    estimator: $L_2$ theory. *Zeitschrift für Wahrscheinlichkeitstheorie
    und Verwandte Gebiete*, 57, 453–476.

6.  Sturges, H. A. (1926). The choice of a class interval. *Journal of
    the American Statistical Association*, 21(153), 65–66.

7.  Wilkinson, L. (1999). The grammar of graphics. Springer.

8.  Wickham, H. (2016). *ggplot2: Elegant Graphics for Data Analysis*.
    Springer.

9.  McCarthy, D. J., Chen, Y., & Smyth, G. K. (2012). Differential
    expression analysis of multifactor RNA-seq experiments with respect
    to biological variation. *Nucleic Acids Research*, 40(10),
    4288–4297.

10. Love, M. I., Huber, W., & Anders, S. (2014). Moderated estimation of
    fold change and dispersion for RNA-seq data with DESeq2. *Genome
    Biology*, 15, 550.

11. R Core Team. *R: A Language and Environment for Statistical
    Computing*. R Foundation for Statistical Computing, Vienna, Austria.

------------------------------------------------------------------------

# 33. Reproducibility Information

``` r
sessionInfo()
```

    ## R version 4.5.3 (2026-03-11 ucrt)
    ## Platform: x86_64-w64-mingw32/x64
    ## Running under: Windows 11 x64 (build 26200)
    ## 
    ## Matrix products: default
    ##   LAPACK version 3.12.1
    ## 
    ## locale:
    ## [1] LC_COLLATE=English_United States.utf8 
    ## [2] LC_CTYPE=English_United States.utf8   
    ## [3] LC_MONETARY=English_United States.utf8
    ## [4] LC_NUMERIC=C                          
    ## [5] LC_TIME=English_United States.utf8    
    ## 
    ## time zone: Asia/Calcutta
    ## tzcode source: internal
    ## 
    ## attached base packages:
    ## [1] stats     graphics  grDevices utils     datasets  methods   base     
    ## 
    ## loaded via a namespace (and not attached):
    ##  [1] compiler_4.5.3    fastmap_1.2.0     cli_3.6.6         tools_4.5.3      
    ##  [5] htmltools_0.5.9   rstudioapi_0.19.0 yaml_2.3.12       rmarkdown_2.31   
    ##  [9] knitr_1.51        xfun_0.57         digest_0.6.39     rlang_1.2.0      
    ## [13] evaluate_1.0.5

> **Next chapter:** Measures of Central Tendency
