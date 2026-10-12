---
title: "Chapter 2: Essential R for Biostatistics"
subtitle: "A Beginner-Friendly Introduction Using Biological Data"
author: "Sandeep Singh"
output:
  github_document:
    toc: true
    toc_depth: 3
    fig_width: 8
    fig_height: 5
    preserve_yaml: true
---

Chapter 2: Essential R for Biostatistics
================
Sandeep Singh

- [1. Introduction](#1-introduction)
- [2. R and RStudio Are Not the Same
  Thing](#2-r-and-rstudio-are-not-the-same-thing)
  - [2.1 R](#21-r)
  - [2.2 RStudio](#22-rstudio)
- [3. Console, Script and
  Environment](#3-console-script-and-environment)
  - [3.1 The console](#31-the-console)
  - [3.2 An R script](#32-an-r-script)
  - [3.3 The environment](#33-the-environment)
- [4. Understanding Basic R Syntax](#4-understanding-basic-r-syntax)
  - [4.1 R is case-sensitive](#41-r-is-case-sensitive)
  - [4.2 Comments](#42-comments)
  - [4.3 Parentheses, brackets and
    braces](#43-parentheses-brackets-and-braces)
- [5. Objects and Assignment](#5-objects-and-assignment)
  - [5.1 Why use `<-`?](#51-why-use--)
  - [5.2 Naming objects](#52-naming-objects)
- [6. R as a Calculator](#6-r-as-a-calculator)
  - [6.1 Order of operations](#61-order-of-operations)
  - [6.2 A biological calculation](#62-a-biological-calculation)
- [7. Functions and Arguments](#7-functions-and-arguments)
  - [7.1 Named arguments](#71-named-arguments)
  - [7.2 Functions can return values](#72-functions-can-return-values)
  - [7.3 Getting help](#73-getting-help)
- [8. Vectors: The Foundation of R](#8-vectors-the-foundation-of-r)
  - [8.1 Creating a vector with `c()`](#81-creating-a-vector-with-c)
  - [8.2 Examining a vector](#82-examining-a-vector)
  - [8.3 Vectorized calculations](#83-vectorized-calculations)
  - [8.4 Combining vectors in
    calculations](#84-combining-vectors-in-calculations)
  - [8.5 Recycling warning](#85-recycling-warning)
- [9. Basic Data Types](#9-basic-data-types)
  - [9.1 Numeric data](#91-numeric-data)
  - [9.2 Integer data](#92-integer-data)
  - [9.3 Character data](#93-character-data)
  - [9.4 Logical data](#94-logical-data)
  - [9.5 Special numeric values](#95-special-numeric-values)
- [10. Coercion: When R Changes a Data
  Type](#10-coercion-when-r-changes-a-data-type)
  - [10.1 Explicit conversion](#101-explicit-conversion)
- [11. Selecting Values from a
  Vector](#11-selecting-values-from-a-vector)
  - [11.1 Selecting by position](#111-selecting-by-position)
  - [11.2 Excluding positions](#112-excluding-positions)
  - [11.3 Selecting a range](#113-selecting-a-range)
  - [11.4 Selecting with a logical
    condition](#114-selecting-with-a-logical-condition)
  - [11.5 Named vectors](#115-named-vectors)
- [12. Comparison and Logical
  Operators](#12-comparison-and-logical-operators)
- [13. Missing Values](#13-missing-values)
  - [13.1 Detecting missing values](#131-detecting-missing-values)
  - [13.2 Missing values affect
    calculations](#132-missing-values-affect-calculations)
  - [13.3 Do not compare missing values with
    `==`](#133-do-not-compare-missing-values-with-)
  - [13.4 Zero is not automatically
    missing](#134-zero-is-not-automatically-missing)
- [14. Factors: Representing
  Categories](#14-factors-representing-categories)
  - [14.1 Reference levels matter](#141-reference-levels-matter)
  - [14.2 Ordered factors](#142-ordered-factors)
- [15. Matrices](#15-matrices)
  - [15.1 Matrix dimensions](#151-matrix-dimensions)
  - [15.2 Selecting matrix values](#152-selecting-matrix-values)
- [16. Data Frames](#16-data-frames)
  - [16.1 Selecting columns](#161-selecting-columns)
  - [16.2 Selecting rows](#162-selecting-rows)
  - [16.3 Selecting rows with
    conditions](#163-selecting-rows-with-conditions)
  - [16.4 Adding a column](#164-adding-a-column)
- [17. Inspecting a Dataset Before
  Analysis](#17-inspecting-a-dataset-before-analysis)
  - [17.1 What these functions tell
    us](#171-what-these-functions-tell-us)
  - [17.2 Useful inspection questions](#172-useful-inspection-questions)
- [18. Basic Summary Functions](#18-basic-summary-functions)
  - [18.1 Counting categories](#181-counting-categories)
  - [18.2 Calculating proportions](#182-calculating-proportions)
  - [18.3 Summarizing by group](#183-summarizing-by-group)
- [19. Importing Data](#19-importing-data)
  - [19.1 CSV files](#191-csv-files)
  - [19.2 Tab-separated files](#192-tab-separated-files)
  - [19.3 Immediately inspect imported
    data](#193-immediately-inspect-imported-data)
  - [19.4 Relative and absolute paths](#194-relative-and-absolute-paths)
- [20. Exporting Data and Results](#20-exporting-data-and-results)
- [21. Basic Figures in R](#21-basic-figures-in-r)
  - [21.1 Scatterplot](#211-scatterplot)
  - [21.2 Boxplot with individual
    observations](#212-boxplot-with-individual-observations)
  - [21.3 Histogram](#213-histogram)
- [22. Packages](#22-packages)
  - [22.1 Installing a package](#221-installing-a-package)
  - [22.2 Loading a package](#222-loading-a-package)
  - [22.3 Installation versus loading](#223-installation-versus-loading)
  - [22.4 Function conflicts](#224-function-conflicts)
- [23. Errors, Warnings and Messages](#23-errors-warnings-and-messages)
  - [23.1 Error](#231-error)
  - [23.2 Warning](#232-warning)
  - [23.3 Message](#233-message)
  - [23.4 A practical debugging
    sequence](#234-a-practical-debugging-sequence)
- [24. Reproducible R Scripts](#24-reproducible-r-scripts)
  - [24.1 Recommended script order](#241-recommended-script-order)
  - [24.2 Use a random seed](#242-use-a-random-seed)
  - [24.3 Avoid manual changes to analysed
    data](#243-avoid-manual-changes-to-analysed-data)
  - [24.4 Test from a clean session](#244-test-from-a-clean-session)
- [25. R Markdown and GitHub
  Markdown](#25-r-markdown-and-github-markdown)
  - [25.1 YAML header](#251-yaml-header)
  - [25.2 R code chunks](#252-r-code-chunks)
  - [25.3 Important chunk options](#253-important-chunk-options)
  - [25.4 Knitting the document](#254-knitting-the-document)
- [26. Integrated Case Study: Biological Sample Quality
  Control](#26-integrated-case-study-biological-sample-quality-control)
  - [26.1 Inspect the dataset](#261-inspect-the-dataset)
  - [26.2 Define transparent quality-control
    rules](#262-define-transparent-quality-control-rules)
  - [26.3 Count passed and failed
    samples](#263-count-passed-and-failed-samples)
  - [26.4 Select samples that passed](#264-select-samples-that-passed)
  - [26.5 Visualize the two QC
    measurements](#265-visualize-the-two-qc-measurements)
- [27. Common Beginner Mistakes](#27-common-beginner-mistakes)
  - [Mistake 1: Using an object before creating
    it](#mistake-1-using-an-object-before-creating-it)
  - [Mistake 2: Confusing `<-` and `==`](#mistake-2-confusing---and-)
  - [Mistake 3: Ignoring uppercase and lowercase
    differences](#mistake-3-ignoring-uppercase-and-lowercase-differences)
  - [Mistake 4: Forgetting quotation marks around
    text](#mistake-4-forgetting-quotation-marks-around-text)
  - [Mistake 5: Comparing missing values with
    `== NA`](#mistake-5-comparing-missing-values-with--na)
  - [Mistake 6: Assuming imported columns have correct data
    types](#mistake-6-assuming-imported-columns-have-correct-data-types)
  - [Mistake 7: Treating zero as automatically
    missing](#mistake-7-treating-zero-as-automatically-missing)
  - [Mistake 8: Installing packages every time a script
    runs](#mistake-8-installing-packages-every-time-a-script-runs)
  - [Mistake 9: Using absolute paths throughout a
    project](#mistake-9-using-absolute-paths-throughout-a-project)
  - [Mistake 10: Clearing errors without reading
    them](#mistake-10-clearing-errors-without-reading-them)
  - [Mistake 11: Trusting an analysis that works only in an old
    environment](#mistake-11-trusting-an-analysis-that-works-only-in-an-old-environment)
- [28. Chapter Summary](#28-chapter-summary)
- [29. Check Your Understanding](#29-check-your-understanding)
  - [Question 1](#question-1)
  - [Question 2](#question-2)
  - [Question 3](#question-3)
  - [Question 4](#question-4)
  - [Question 5](#question-5)
  - [Question 6](#question-6)
  - [Question 7](#question-7)
  - [Question 8](#question-8)
- [30. Practice with R](#30-practice-with-r)
  - [Exercise 1: Create biological
    objects](#exercise-1-create-biological-objects)
  - [Exercise 2: Work with a vector](#exercise-2-work-with-a-vector)
  - [Exercise 3: Work with missing
    data](#exercise-3-work-with-missing-data)
  - [Exercise 4: Create a factor](#exercise-4-create-a-factor)
  - [Exercise 5: Explore a data frame](#exercise-5-explore-a-data-frame)
  - [Exercise 6: Find and correct
    problems](#exercise-6-find-and-correct-problems)
- [31. Mini-Project: Build and Explore a Small Biological
  Dataset](#31-mini-project-build-and-explore-a-small-biological-dataset)
- [32. Glossary](#32-glossary)
- [33. References and Further
  Reading](#33-references-and-further-reading)
- [34. Reproducibility Information](#34-reproducibility-information)

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
table.chapter-table th,
table.chapter-table td {
  border: 1px solid #d0d7de;
  padding: 0.45rem 0.65rem;
  text-align: left;
  vertical-align: top;
}
table.chapter-table th {
  background-color: #f6f8fa;
  font-weight: 600;
}
table.chapter-table caption {
  margin-bottom: 0.5rem;
  font-weight: 600;
  text-align: left;
}
</style>

# 1. Introduction

Biostatistics is not learned by reading formulas alone. We must also
work with data, calculate summaries, produce figures and examine whether
our results make biological sense.

R is a programming language and statistical environment designed for
these tasks. It is widely used in statistics, epidemiology, genetics,
genomics, bioinformatics and data science.

In this chapter, we will learn only the R foundations needed for the
statistical chapters that follow. Every important idea will be
introduced using simple biological examples.

No previous programming knowledge is required.

> **The objective is not to memorize every R command. The objective is
> to understand how data are represented and how instructions are given
> to R.**

------------------------------------------------------------------------

# 2. R and RStudio Are Not the Same Thing

Beginners often use the words **R** and **RStudio** as if they mean the
same thing. They do not.

## 2.1 R

R is the language and computational engine that performs the analysis.

R can:

- calculate means and standard deviations;
- perform statistical tests;
- fit regression models;
- generate figures;
- simulate biological data;
- analyse genetic and genomic datasets; and
- create reproducible reports.

## 2.2 RStudio

RStudio is an integrated development environment, commonly called an
**IDE**. It provides a convenient interface for working with R.

RStudio normally contains four main panes:

| Pane | Main purpose |
|----|----|
| Source | Write and save scripts or R Markdown files |
| Console | Run R commands and view immediate output |
| Environment/History | Inspect created objects and previous commands |
| Files/Plots/Packages/Help | Browse files, view figures, manage packages and read documentation |

You can think of R as the **engine** and RStudio as the **dashboard**
used to control the engine.

------------------------------------------------------------------------

# 3. Console, Script and Environment

## 3.1 The console

The console is useful for quick calculations and experiments.

``` r
12 + 8
```

    ## [1] 20

The console executes a command immediately after you press Enter.
However, commands typed only in the console are easy to lose and
difficult to reproduce.

## 3.2 An R script

An R script is a plain-text file normally saved with the extension `.R`.

Use a script when you want to:

- save your analysis;
- run the analysis again;
- correct or improve your code;
- share the workflow; or
- document how a result was produced.

In RStudio, a selected line can usually be run with **Ctrl + Enter** on
Windows or Linux and **Command + Enter** on macOS.

## 3.3 The environment

The R environment contains the objects created during the current
session.

``` r
gene_name <- "TP53"
sample_count <- 24
mean_expression <- 8.7
```

The objects `gene_name`, `sample_count` and `mean_expression` now exist
in memory.

Use `ls()` to list objects in the current environment.

``` r
ls()
```

    ## [1] "gene_name"             "mean_expression"       "prepare_display_table"
    ## [4] "print_html_table"      "sample_count"

An object exists only after the code that creates it has been executed.

------------------------------------------------------------------------

# 4. Understanding Basic R Syntax

Syntax means the rules used to write instructions in a programming
language.

## 4.1 R is case-sensitive

R treats uppercase and lowercase letters as different.

``` r
gene <- "BRCA1"
Gene <- "BRCA2"

gene
```

    ## [1] "BRCA1"

``` r
Gene
```

    ## [1] "BRCA2"

The objects `gene` and `Gene` are separate objects.

## 4.2 Comments

A comment begins with `#`. R does not execute text appearing after `#`
on the same line.

``` r
# Store the number of biological samples
n_samples <- 12

# Calculate twice the number of samples
2 * n_samples
```

    ## [1] 24

Comments should explain the reason for an analytical decision, not
merely repeat obvious code.

Less useful comment:

``` r
# Calculate the mean
mean(expression)
```

More useful comment:

``` r
# Summarize expression after excluding measurements that failed quality control
mean(expression_qc_pass)
```

## 4.3 Parentheses, brackets and braces

These symbols have different purposes:

| Symbol | Common use |
|----|----|
| `()` | Supply arguments to a function |
| `[]` | Select elements from an object |
| `{}` | Group several instructions, especially inside functions or conditions |

We will use parentheses and brackets frequently in this chapter. Braces
will become more important when programming concepts are introduced
later.

------------------------------------------------------------------------

# 5. Objects and Assignment

An **object** is a named place where R stores information.

The assignment operator `<-` stores the value on its right inside the
object named on its left.

``` r
patient_age <- 46
gene_symbol <- "CYP2C19"
treatment_response <- TRUE

patient_age
```

    ## [1] 46

``` r
gene_symbol
```

    ## [1] "CYP2C19"

``` r
treatment_response
```

    ## [1] TRUE

Read the first instruction as:

> Store the value 46 in an object called `patient_age`.

## 5.1 Why use `<-`?

R also permits `=` in many assignment situations, but `<-` clearly
distinguishes object assignment from named function arguments. This book
will use `<-` consistently.

## 5.2 Naming objects

Good object names describe their contents.

``` r
control_expression <- 7.8
treated_expression <- 10.2
```

Recommended practices:

- use meaningful names;
- use lowercase letters;
- separate words with underscores;
- avoid spaces;
- avoid beginning a name with a number; and
- avoid names such as `data`, `mean`, `c`, `T` and `F` that may hide
  existing R functions or constants.

| Poor name | Better name       |
|-----------|-------------------|
| `x`       | `gene_expression` |
| `a1`      | `patient_age`     |
| `my data` | `clinical_data`   |
| `mean`    | `mean_glucose`    |

Short names such as `x` and `y` are acceptable in small mathematical
examples, but meaningful names are safer in real analyses.

------------------------------------------------------------------------

# 6. R as a Calculator

R supports standard arithmetic operations.

| Operation        | R operator | Example   |
|------------------|------------|-----------|
| Addition         | `+`        | `5 + 3`   |
| Subtraction      | `-`        | `5 - 3`   |
| Multiplication   | `*`        | `5 * 3`   |
| Division         | `/`        | `5 / 3`   |
| Exponentiation   | `^`        | `5^2`     |
| Remainder        | `%%`       | `5 %% 3`  |
| Integer division | `%/%`      | `5 %/% 3` |

``` r
5 + 3
```

    ## [1] 8

``` r
5 - 3
```

    ## [1] 2

``` r
5 * 3
```

    ## [1] 15

``` r
5 / 3
```

    ## [1] 1.666667

``` r
5^2
```

    ## [1] 25

``` r
5 %% 3
```

    ## [1] 2

``` r
5 %/% 3
```

    ## [1] 1

## 6.1 Order of operations

R follows the usual mathematical order of operations. Use parentheses
when they make the intended calculation clearer.

``` r
5 + 2 * 3
```

    ## [1] 11

``` r
(5 + 2) * 3
```

    ## [1] 21

## 6.2 A biological calculation

Suppose 18 of 24 tissue samples pass quality control.

``` r
passed_samples <- 18
total_samples <- 24

qc_pass_percentage <-
  (passed_samples / total_samples) * 100

qc_pass_percentage
```

    ## [1] 75

The result is a percentage because the proportion was multiplied by 100.

------------------------------------------------------------------------

# 7. Functions and Arguments

A **function** is a reusable instruction that performs a task.

The general structure is:

``` r
function_name(argument_1, argument_2)
```

For example, `sqrt()` calculates a square root.

``` r
sqrt(144)
```

    ## [1] 12

The value `144` is an **argument** supplied to the function.

## 7.1 Named arguments

Some functions accept several arguments. Naming them makes code easier
to understand.

``` r
round(x = 3.14159, digits = 2)
```

    ## [1] 3.14

## 7.2 Functions can return values

The result of a function can be stored in an object.

``` r
rounded_value <- round(x = 3.14159, digits = 2)
rounded_value
```

    ## [1] 3.14

## 7.3 Getting help

Use `?` or `help()` to open the documentation for a function.

``` r
?mean
help(mean)
```

If you do not know the exact function name, use `help.search()`.

``` r
help.search("standard deviation")
```

R documentation may feel difficult initially. Focus first on:

- **Usage** — how the function is written;
- **Arguments** — what information the function accepts;
- **Value** — what the function returns; and
- **Examples** — working demonstrations.

------------------------------------------------------------------------

# 8. Vectors: The Foundation of R

A **vector** is a one-dimensional collection of values of the same basic
type.

Vectors are fundamental because many biological measurements can be
represented as a series of values.

Examples include:

- patient ages;
- plant heights;
- gene-expression values;
- DNA-fragment lengths;
- treatment labels; and
- quality-control outcomes.

## 8.1 Creating a vector with `c()`

The `c()` function combines values.

``` r
plant_height <- c(12.1, 13.4, 11.8, 14.2, 12.9)
gene_names <- c("TP53", "BRCA1", "EGFR", "APOE")
qc_pass <- c(TRUE, TRUE, FALSE, TRUE)

plant_height
```

    ## [1] 12.1 13.4 11.8 14.2 12.9

``` r
gene_names
```

    ## [1] "TP53"  "BRCA1" "EGFR"  "APOE"

``` r
qc_pass
```

    ## [1]  TRUE  TRUE FALSE  TRUE

## 8.2 Examining a vector

``` r
length(plant_height)
```

    ## [1] 5

``` r
class(plant_height)
```

    ## [1] "numeric"

``` r
typeof(plant_height)
```

    ## [1] "double"

``` r
str(plant_height)
```

    ##  num [1:5] 12.1 13.4 11.8 14.2 12.9

These functions answer different questions:

| Function   | Question answered                    |
|------------|--------------------------------------|
| `length()` | How many elements are present?       |
| `class()`  | How does R treat the object?         |
| `typeof()` | How is the object stored internally? |
| `str()`    | What is its compact structure?       |

## 8.3 Vectorized calculations

R can perform the same calculation on every element without an explicit
loop.

Suppose DNA-fragment lengths are recorded in base pairs and we want
their lengths in kilobases.

``` r
fragment_bp <- c(850, 1200, 1750, 2300)
fragment_kb <- fragment_bp / 1000

fragment_kb
```

    ## [1] 0.85 1.20 1.75 2.30

This is called a **vectorized operation**.

## 8.4 Combining vectors in calculations

``` r
control_expression <- c(7.2, 7.8, 8.1, 7.5)
treated_expression <- c(9.4, 10.1, 9.8, 10.3)

expression_difference <-
  treated_expression - control_expression

expression_difference
```

    ## [1] 2.2 2.3 1.7 2.8

R subtracts corresponding elements. This calculation makes sense only if
the two vectors have compatible lengths and correctly aligned
observations.

## 8.5 Recycling warning

If vector lengths differ, R may repeat values from the shorter vector.
This is called **recycling** and can cause unnoticed errors.

``` r
c(10, 20, 30, 40) + c(1, 2)
```

    ## [1] 11 22 31 42

R repeats `1, 2` to obtain `1, 2, 1, 2`.

Avoid relying on recycling unless it is deliberate and obvious.

------------------------------------------------------------------------

# 9. Basic Data Types

## 9.1 Numeric data

Numeric values include decimal measurements.

``` r
body_temperature <- c(36.8, 37.1, 36.6)
typeof(body_temperature)
```

    ## [1] "double"

## 9.2 Integer data

Integers are whole numbers stored using an `L` suffix when created
explicitly.

``` r
mutation_count <- c(4L, 7L, 2L)
typeof(mutation_count)
```

    ## [1] "integer"

## 9.3 Character data

Character values are text enclosed in quotation marks.

``` r
tissue_type <- c("Blood", "Liver", "Brain")
typeof(tissue_type)
```

    ## [1] "character"

## 9.4 Logical data

Logical values are `TRUE` or `FALSE`.

``` r
sample_passed_qc <- c(TRUE, FALSE, TRUE)
typeof(sample_passed_qc)
```

    ## [1] "logical"

Do not place quotation marks around logical values. `TRUE` is logical,
while `"TRUE"` is character text.

## 9.5 Special numeric values

R also recognizes:

- `Inf` for positive infinity;
- `-Inf` for negative infinity; and
- `NaN` for an undefined numerical result.

``` r
1 / 0
```

    ## [1] Inf

``` r
0 / 0
```

    ## [1] NaN

These values are different from missing data, which are represented by
`NA`.

------------------------------------------------------------------------

# 10. Coercion: When R Changes a Data Type

A basic vector can contain only one underlying data type. If different
types are combined, R converts them to a common type.

``` r
mixed_values <- c(25, "Blood", TRUE)

mixed_values
```

    ## [1] "25"    "Blood" "TRUE"

``` r
typeof(mixed_values)
```

    ## [1] "character"

All values become character text because character data can represent
the other entries.

This can happen accidentally during data import. A numeric laboratory
column may become character if one entry contains text such as
`"not measured"`.

## 10.1 Explicit conversion

Common conversion functions include:

- `as.numeric()`;
- `as.integer()`;
- `as.character()`;
- `as.logical()`; and
- `as.factor()`.

``` r
read_count_text <- c("120", "145", "98")
read_count_numeric <- as.numeric(read_count_text)

read_count_numeric
```

    ## [1] 120 145  98

``` r
typeof(read_count_numeric)
```

    ## [1] "double"

Always inspect values before converting them. A conversion warning may
indicate that some entries cannot be converted safely.

------------------------------------------------------------------------

# 11. Selecting Values from a Vector

Selection is also called **indexing** or **subsetting**.

``` r
gene_expression <- c(8.2, 7.6, 10.4, 9.1, 11.3)
```

## 11.1 Selecting by position

``` r
gene_expression[1]
```

    ## [1] 8.2

``` r
gene_expression[3]
```

    ## [1] 10.4

``` r
gene_expression[c(1, 3, 5)]
```

    ## [1]  8.2 10.4 11.3

R positions begin at 1, not 0.

## 11.2 Excluding positions

``` r
gene_expression[-2]
```

    ## [1]  8.2 10.4  9.1 11.3

This returns all elements except the second.

## 11.3 Selecting a range

``` r
gene_expression[2:4]
```

    ## [1]  7.6 10.4  9.1

## 11.4 Selecting with a logical condition

``` r
gene_expression > 9
```

    ## [1] FALSE FALSE  TRUE  TRUE  TRUE

``` r
gene_expression[gene_expression > 9]
```

    ## [1] 10.4  9.1 11.3

The first instruction creates logical values. The second uses those
logical values to retain only measurements greater than 9.

## 11.5 Named vectors

``` r
expression_by_gene <- c(
  TP53 = 8.2,
  BRCA1 = 7.6,
  EGFR = 10.4,
  APOE = 9.1
)

expression_by_gene["EGFR"]
```

    ## EGFR 
    ## 10.4

Names can make small vectors easier to interpret.

------------------------------------------------------------------------

# 12. Comparison and Logical Operators

Logical conditions are essential for filtering data and defining groups.

| Meaning | Operator | Example |
|----|----|----|
| Equal to | `==` | `status == "Case"` |
| Not equal to | `!=` | `status != "Case"` |
| Greater than | `>` | `age > 50` |
| Less than | `<` | `age < 50` |
| Greater than or equal to | `>=` | `quality >= 30` |
| Less than or equal to | `<=` | `quality <= 30` |
| AND | `&` | `age > 40 & status == "Case"` |
| OR | `\|` | `status == "Case" \| status == "Control"` |
| NOT | `!` | `!qc_pass` |
| Included in a set | `%in%` | `gene %in% c("TP53", "EGFR")` |

``` r
sample_quality <- c(35, 28, 41, 19, 33)

sample_quality >= 30
```

    ## [1]  TRUE FALSE  TRUE FALSE  TRUE

``` r
sample_quality[sample_quality >= 30]
```

    ## [1] 35 41 33

Use `==` when comparing values. A single `<-` assigns a value and does
not test equality.

------------------------------------------------------------------------

# 13. Missing Values

Missing information is represented by `NA`.

``` r
glucose <- c(92, 105, NA, 110, 98)
glucose
```

    ## [1]  92 105  NA 110  98

## 13.1 Detecting missing values

``` r
is.na(glucose)
```

    ## [1] FALSE FALSE  TRUE FALSE FALSE

``` r
sum(is.na(glucose))
```

    ## [1] 1

``` r
anyNA(glucose)
```

    ## [1] TRUE

## 13.2 Missing values affect calculations

``` r
mean(glucose)
```

    ## [1] NA

``` r
mean(glucose, na.rm = TRUE)
```

    ## [1] 101.25

The argument `na.rm = TRUE` tells R to remove missing values for that
calculation.

It does not permanently delete the missing entries from the dataset.

## 13.3 Do not compare missing values with `==`

Incorrect:

``` r
glucose == NA
```

    ## [1] NA NA NA NA NA

Correct:

``` r
is.na(glucose)
```

    ## [1] FALSE FALSE  TRUE FALSE FALSE

## 13.4 Zero is not automatically missing

A zero can be a valid biological measurement.

Examples include:

- zero detected colonies;
- zero copies of an effect allele;
- zero observed adverse events; or
- zero sequencing reads for a feature.

Whether zero represents a valid measurement or an encoded missing value
depends on the data documentation and scientific context.

------------------------------------------------------------------------

# 14. Factors: Representing Categories

A **factor** represents categorical data with a defined set of possible
categories called **levels**.

``` r
treatment <- factor(
  c("Control", "Treated", "Control", "Treated")
)

treatment
```

    ## [1] Control Treated Control Treated
    ## Levels: Control Treated

``` r
levels(treatment)
```

    ## [1] "Control" "Treated"

## 14.1 Reference levels matter

In many statistical models, one category becomes the reference group.

``` r
treatment <- relevel(treatment, ref = "Control")
levels(treatment)
```

    ## [1] "Control" "Treated"

This makes `Control` the reference level.

## 14.2 Ordered factors

Some categories have a meaningful order.

``` r
disease_severity <- factor(
  c("Mild", "Severe", "Moderate", "Mild"),
  levels = c("Mild", "Moderate", "Severe"),
  ordered = TRUE
)

disease_severity
```

    ## [1] Mild     Severe   Moderate Mild    
    ## Levels: Mild < Moderate < Severe

Although the levels are ordered, the distance between `Mild` and
`Moderate` is not automatically numerical.

------------------------------------------------------------------------

# 15. Matrices

A **matrix** is a two-dimensional structure in which every value has the
same basic type.

Matrices are common in bioinformatics. A gene-expression matrix may
contain genes in rows and samples in columns.

``` r
expression_matrix <- matrix(
  c(
    8.1, 7.9, 10.2,
    6.5, 6.8, 9.4
  ),
  nrow = 2,
  byrow = TRUE
)

rownames(expression_matrix) <- c("Gene_A", "Gene_B")
colnames(expression_matrix) <- c(
  "Control_1",
  "Control_2",
  "Treated_1"
)

print_html_table(
  expression_matrix,
  caption = "Example gene-expression matrix."
)
```

<table class="chapter-table">

<caption>

Example gene-expression matrix.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

Control 1
</th>

<th style="text-align:right;">

Control 2
</th>

<th style="text-align:right;">

Treated 1
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Gene_A
</td>

<td style="text-align:right;">

8.1
</td>

<td style="text-align:right;">

7.9
</td>

<td style="text-align:right;">

10.2
</td>

</tr>

<tr>

<td style="text-align:left;">

Gene_B
</td>

<td style="text-align:right;">

6.5
</td>

<td style="text-align:right;">

6.8
</td>

<td style="text-align:right;">

9.4
</td>

</tr>

</tbody>

</table>

## 15.1 Matrix dimensions

``` r
dim(expression_matrix)
```

    ## [1] 2 3

``` r
nrow(expression_matrix)
```

    ## [1] 2

``` r
ncol(expression_matrix)
```

    ## [1] 3

## 15.2 Selecting matrix values

Matrices use `[row, column]` indexing.

``` r
expression_matrix[1, 2]
```

    ## [1] 7.9

``` r
expression_matrix["Gene_B", "Treated_1"]
```

    ## [1] 9.4

``` r
expression_matrix[1, ]
```

    ## Control_1 Control_2 Treated_1 
    ##       8.1       7.9      10.2

``` r
expression_matrix[, 3]
```

    ## Gene_A Gene_B 
    ##   10.2    9.4

Leaving the column position empty selects every column. Leaving the row
position empty selects every row.

------------------------------------------------------------------------

# 16. Data Frames

A **data frame** is a two-dimensional table in which different columns
may contain different data types.

This makes data frames suitable for clinical and biological datasets.

``` r
sample_data <- data.frame(
  sample_id = c("S01", "S02", "S03", "S04", "S05", "S06"),
  tissue = c("Blood", "Blood", "Liver", "Liver", "Blood", "Liver"),
  treatment = c("Control", "Treated", "Control", "Treated", "Control", "Treated"),
  expression = c(8.2, 10.1, 7.5, 9.8, 8.7, 10.4),
  qc_pass = c(TRUE, TRUE, FALSE, TRUE, TRUE, TRUE),
  stringsAsFactors = FALSE
)

print_html_table(
  sample_data,
  caption = "Example biological sample data."
)
```

<table class="chapter-table">

<caption>

Example biological sample data.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.2
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.1
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

7.5
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

9.8
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.7
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.4
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

Each row is one biological sample. Each column is one variable.

## 16.1 Selecting columns

The `$` operator selects a column by name.

``` r
sample_data$expression
```

    ## [1]  8.2 10.1  7.5  9.8  8.7 10.4

Columns can also be selected with brackets.

``` r
sample_data[, "expression"]
```

    ## [1]  8.2 10.1  7.5  9.8  8.7 10.4

``` r
print_html_table(
  sample_data[, c("sample_id", "expression")],
  caption = "Selected sample identifier and expression columns."
)
```

<table class="chapter-table">

<caption>

Selected sample identifier and expression columns.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:right;">

expression
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:right;">

8.2
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:right;">

10.1
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:right;">

7.5
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:right;">

9.8
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:right;">

8.7
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:right;">

10.4
</td>

</tr>

</tbody>

</table>

## 16.2 Selecting rows

``` r
print_html_table(
  sample_data[1, ],
  caption = "The first observation."
)
```

<table class="chapter-table">

<caption>

The first observation.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.2
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

``` r
print_html_table(
  sample_data[1:3, ],
  caption = "The first three observations."
)
```

<table class="chapter-table">

<caption>

The first three observations.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.2
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.1
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

7.5
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

</tbody>

</table>

## 16.3 Selecting rows with conditions

``` r
print_html_table(
  sample_data[sample_data$qc_pass, ],
  caption = "Samples that passed quality control."
)
```

<table class="chapter-table">

<caption>

Samples that passed quality control.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.2
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.1
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

9.8
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.7
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.4
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

``` r
print_html_table(
  sample_data[
    sample_data$treatment == "Treated" &
      sample_data$qc_pass,
  ],
  caption = "Treated samples that passed quality control."
)
```

<table class="chapter-table">

<caption>

Treated samples that passed quality control.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.1
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

9.8
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.4
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

## 16.4 Adding a column

``` r
sample_data$expression_high <-
  sample_data$expression >= 9

print_html_table(
  sample_data,
  caption = "Sample data after adding the expression-high indicator."
)
```

<table class="chapter-table">

<caption>

Sample data after adding the expression-high indicator.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

<th style="text-align:left;">

expression high
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.2
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.1
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

7.5
</td>

<td style="text-align:left;">

FALSE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

9.8
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.7
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.4
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

The comparison creates `TRUE` or `FALSE` for each row.

------------------------------------------------------------------------

# 17. Inspecting a Dataset Before Analysis

Never begin a statistical analysis without first inspecting the dataset.

``` r
print_html_table(
  head(sample_data),
  caption = "First observations in the sample dataset."
)
```

<table class="chapter-table">

<caption>

First observations in the sample dataset.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

<th style="text-align:left;">

expression high
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.2
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.1
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

7.5
</td>

<td style="text-align:left;">

FALSE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

9.8
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.7
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.4
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

``` r
print_html_table(
  tail(sample_data),
  caption = "Last observations in the sample dataset."
)
```

<table class="chapter-table">

<caption>

Last observations in the sample dataset.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

tissue
</th>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

<th style="text-align:left;">

qc pass
</th>

<th style="text-align:left;">

expression high
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.2
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.1
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

7.5
</td>

<td style="text-align:left;">

FALSE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

9.8
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.7
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.4
</td>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

``` r
dim(sample_data)
```

    ## [1] 6 6

``` r
nrow(sample_data)
```

    ## [1] 6

``` r
ncol(sample_data)
```

    ## [1] 6

``` r
names(sample_data)
```

    ## [1] "sample_id"       "tissue"          "treatment"       "expression"     
    ## [5] "qc_pass"         "expression_high"

``` r
str(sample_data)
```

    ## 'data.frame':    6 obs. of  6 variables:
    ##  $ sample_id      : chr  "S01" "S02" "S03" "S04" ...
    ##  $ tissue         : chr  "Blood" "Blood" "Liver" "Liver" ...
    ##  $ treatment      : chr  "Control" "Treated" "Control" "Treated" ...
    ##  $ expression     : num  8.2 10.1 7.5 9.8 8.7 10.4
    ##  $ qc_pass        : logi  TRUE TRUE FALSE TRUE TRUE TRUE
    ##  $ expression_high: logi  FALSE TRUE FALSE TRUE FALSE TRUE

``` r
summary(sample_data)
```

    ##   sample_id            tissue           treatment           expression    
    ##  Length:6           Length:6           Length:6           Min.   : 7.500  
    ##  Class :character   Class :character   Class :character   1st Qu.: 8.325  
    ##  Mode  :character   Mode  :character   Mode  :character   Median : 9.250  
    ##                                                           Mean   : 9.117  
    ##                                                           3rd Qu.:10.025  
    ##                                                           Max.   :10.400  
    ##   qc_pass        expression_high
    ##  Mode :logical   Mode :logical  
    ##  FALSE:1         FALSE:3        
    ##  TRUE :5         TRUE :3        
    ##                                 
    ##                                 
    ## 

## 17.1 What these functions tell us

| Function    | Information provided          |
|-------------|-------------------------------|
| `head()`    | First observations            |
| `tail()`    | Last observations             |
| `dim()`     | Number of rows and columns    |
| `nrow()`    | Number of rows                |
| `ncol()`    | Number of columns             |
| `names()`   | Column names                  |
| `str()`     | Structure and data types      |
| `summary()` | Basic summary of every column |

## 17.2 Useful inspection questions

Before analysis, ask:

- Does each row represent the intended observational unit?
- Are column names understandable?
- Are numeric variables stored as numeric?
- Are categories spelled consistently?
- Are missing values represented correctly?
- Are measurement units documented?
- Are any values biologically impossible?
- Are sample identifiers unique?

------------------------------------------------------------------------

# 18. Basic Summary Functions

``` r
expression_values <- sample_data$expression

length(expression_values)
```

    ## [1] 6

``` r
mean(expression_values)
```

    ## [1] 9.116667

``` r
median(expression_values)
```

    ## [1] 9.25

``` r
sd(expression_values)
```

    ## [1] 1.158303

``` r
var(expression_values)
```

    ## [1] 1.341667

``` r
min(expression_values)
```

    ## [1] 7.5

``` r
max(expression_values)
```

    ## [1] 10.4

``` r
range(expression_values)
```

    ## [1]  7.5 10.4

``` r
quantile(expression_values)
```

    ##     0%    25%    50%    75%   100% 
    ##  7.500  8.325  9.250 10.025 10.400

These functions describe the observed sample. Later chapters will
explain their statistical meaning and appropriate use in detail.

## 18.1 Counting categories

``` r
print_html_table(
  table(sample_data$tissue),
  caption = "Tissue frequencies."
)
```

<table class="chapter-table">

<caption>

Tissue frequencies.
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

Blood
</td>

<td style="text-align:right;">

3
</td>

</tr>

<tr>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:right;">

3
</td>

</tr>

</tbody>

</table>

``` r
print_html_table(
  table(sample_data$treatment),
  caption = "Treatment-group frequencies."
)
```

<table class="chapter-table">

<caption>

Treatment-group frequencies.
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

Control
</td>

<td style="text-align:right;">

3
</td>

</tr>

<tr>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

3
</td>

</tr>

</tbody>

</table>

``` r
print_html_table(
  table(sample_data$treatment, sample_data$qc_pass),
  caption = "Treatment group by quality-control status."
)
```

<table class="chapter-table">

<caption>

Treatment group by quality-control status.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Category
</th>

<th style="text-align:right;">

FALSE.
</th>

<th style="text-align:right;">

TRUE.
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

1
</td>

<td style="text-align:right;">

2
</td>

</tr>

<tr>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

0
</td>

<td style="text-align:right;">

3
</td>

</tr>

</tbody>

</table>

## 18.2 Calculating proportions

``` r
tissue_proportions <- prop.table(table(sample_data$tissue))
print_html_table(
  data.frame(
    Tissue = names(tissue_proportions),
    Proportion = as.numeric(tissue_proportions)
  ),
  caption = "Proportion of samples from each tissue."
)
```

<table class="chapter-table">

<caption>

Proportion of samples from each tissue.
</caption>

<thead>

<tr>

<th style="text-align:left;">

Tissue
</th>

<th style="text-align:right;">

Proportion
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Blood
</td>

<td style="text-align:right;">

0.5
</td>

</tr>

<tr>

<td style="text-align:left;">

Liver
</td>

<td style="text-align:right;">

0.5
</td>

</tr>

</tbody>

</table>

## 18.3 Summarizing by group

``` r
mean_by_treatment <- aggregate(
  expression ~ treatment,
  data = sample_data,
  FUN = mean
)

print_html_table(
  mean_by_treatment,
  caption = "Mean expression by treatment group."
)
```

<table class="chapter-table">

<caption>

Mean expression by treatment group.
</caption>

<thead>

<tr>

<th style="text-align:left;">

treatment
</th>

<th style="text-align:right;">

expression
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

8.133
</td>

</tr>

<tr>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

10.100
</td>

</tr>

</tbody>

</table>

The output reports the sample mean in each treatment group. It does not
by itself establish a treatment effect.

------------------------------------------------------------------------

# 19. Importing Data

Biological data are often stored in CSV or tab-separated text files.

## 19.1 CSV files

A comma-separated values file can be imported with `read.csv()`.

``` r
clinical_data <- read.csv(
  "data/clinical_data.csv",
  stringsAsFactors = FALSE
)
```

## 19.2 Tab-separated files

``` r
expression_data <- read.delim(
  "data/gene_expression.tsv",
  stringsAsFactors = FALSE
)
```

## 19.3 Immediately inspect imported data

``` r
dim(clinical_data)
names(clinical_data)
str(clinical_data)
head(clinical_data)
summary(clinical_data)
```

Successful import does not guarantee correct import. Always check the
dimensions, column names, data types and example values.

## 19.4 Relative and absolute paths

An absolute path describes the complete location of a file on one
computer. A relative path describes a file location relative to the
project directory.

Absolute path:

``` r
"C:/Users/Student/Desktop/project/data/clinical_data.csv"
```

Relative path:

``` r
"data/clinical_data.csv"
```

Relative paths are preferable because they make a project easier to move
and share.

> **Place data, scripts and outputs inside a clearly organized project
> and use relative paths whenever possible.**

------------------------------------------------------------------------

# 20. Exporting Data and Results

Use `write.csv()` to save a data frame as a CSV file.

``` r
write.csv(
  sample_data,
  "outputs/clean_sample_data.csv",
  row.names = FALSE
)
```

The argument `row.names = FALSE` prevents R from writing row numbers as
an additional column.

Do not overwrite raw data with cleaned or transformed data. A safer
structure is:

``` text
project/
├── data_raw/
├── data_clean/
├── scripts/
├── figures/
└── reports/
```

Raw data should remain unchanged. Corrections and transformations should
be performed through documented code.

------------------------------------------------------------------------

# 21. Basic Figures in R

Statistical graphics allow us to see patterns that may be hidden in
numerical summaries.

## 21.1 Scatterplot

Suppose we measure sequencing read length and quality score for eight
reads.

``` r
read_length <- c(75, 90, 105, 120, 135, 150, 165, 180)
quality_score <- c(24, 26, 27, 29, 31, 32, 34, 35)
```

``` r
plot(
  x = read_length,
  y = quality_score,
  pch = 19,
  col = "steelblue4",
  xlab = "Read length (base pairs)",
  ylab = "Quality score",
  main = "Read length and sequencing quality"
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_02_Essential_R_for_Biostatistics_files/figure-gfm/scatterplot-1.png" alt="A scatterplot showing the relationship between sequencing read length and quality score in a hypothetical dataset." width="85%" />
<p class="caption">

A scatterplot showing the relationship between sequencing read length
and quality score in a hypothetical dataset.
</p>

</div>

Each point represents one sequencing read. The plot shows an increasing
pattern in this hypothetical example, but it does not establish
causation.

## 21.2 Boxplot with individual observations

``` r
boxplot(
  expression ~ treatment,
  data = sample_data,
  col = c("lightblue", "lightpink"),
  xlab = "Treatment group",
  ylab = "Relative gene expression",
  main = "Expression by treatment group"
)

stripchart(
  expression ~ treatment,
  data = sample_data,
  vertical = TRUE,
  method = "jitter",
  pch = 19,
  col = "navy",
  add = TRUE
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_02_Essential_R_for_Biostatistics_files/figure-gfm/expression-boxplot-1.png" alt="Gene-expression values in control and treated biological samples." width="85%" />
<p class="caption">

Gene-expression values in control and treated biological samples.
</p>

</div>

Showing individual observations is especially useful when the sample is
small.

## 21.3 Histogram

``` r
simulated_gene_counts <- rpois(
  n = 100,
  lambda = 20
)
```

``` r
hist(
  simulated_gene_counts,
  breaks = 12,
  col = "darkseagreen2",
  border = "white",
  xlab = "Read count",
  main = "Distribution of simulated gene counts"
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_02_Essential_R_for_Biostatistics_files/figure-gfm/histogram-1.png" alt="Distribution of 100 hypothetical gene read counts simulated from a Poisson distribution." width="85%" />
<p class="caption">

Distribution of 100 hypothetical gene read counts simulated from a
Poisson distribution.
</p>

</div>

The Poisson distribution will be explained in a later chapter. Here, the
example simply demonstrates how `hist()` displays the distribution of
numerical values.

------------------------------------------------------------------------

# 22. Packages

Base R contains many functions, but additional functions are distributed
in **packages**.

A package may contain:

- functions;
- example datasets;
- documentation;
- tutorials; and
- supporting code.

## 22.1 Installing a package

A package normally needs to be installed only once for a particular R
installation.

``` r
install.packages("ggplot2")
```

## 22.2 Loading a package

A package must usually be loaded in each new R session before its
functions are used.

``` r
library(ggplot2)
```

## 22.3 Installation versus loading

| Command | Purpose | Typical frequency |
|----|----|----|
| `install.packages()` | Downloads and installs a package | Usually once |
| `library()` | Makes an installed package available | Each new session or script |

Do not place `install.packages()` inside an analysis script that will be
run repeatedly. Record required packages separately and load them near
the beginning of the script.

## 22.4 Function conflicts

Different packages may contain functions with the same name. The `::`
operator identifies the package explicitly.

``` r
dplyr::filter(sample_data, qc_pass)
stats::filter
```

Package conflicts are not always errors, but they should be recognized
and managed deliberately.

------------------------------------------------------------------------

# 23. Errors, Warnings and Messages

R communicates different kinds of information.

## 23.1 Error

An error means the requested operation could not be completed.

``` r
mean(gene_expresion)
```

If the correct object is `gene_expression`, this code fails because the
name is misspelled.

## 23.2 Warning

A warning means R completed the operation but detected a possible
problem.

``` r
as.numeric(c("10", "not_measured", "12"))
```

R converts valid numbers but warns that `"not_measured"` cannot be
converted numerically.

## 23.3 Message

A message provides information about an operation. It does not
necessarily indicate a problem.

## 23.4 A practical debugging sequence

When code fails:

1.  read the complete error message;
2.  identify the line or chunk that failed;
3.  check object and column names;
4.  inspect the object with `str()`;
5.  confirm that earlier code was executed;
6.  simplify the problem to the smallest failing example;
7.  read the function documentation; and
8.  rerun the script from a clean session after correcting the problem.

Do not repeatedly change unrelated lines without understanding the
error.

------------------------------------------------------------------------

# 24. Reproducible R Scripts

A reproducible script should produce the same result when run again with
the same inputs and software environment.

## 24.1 Recommended script order

``` r
# 1. Project description
# 2. Load required packages
# 3. Import data
# 4. Inspect and clean data
# 5. Create derived variables
# 6. Perform analysis
# 7. Generate tables and figures
# 8. Save outputs
# 9. Record session information
```

## 24.2 Use a random seed

Random operations may produce different results each time. `set.seed()`
makes a simulation reproducible.

``` r
set.seed(42)
sample(1:100, size = 5)
```

    ## [1] 49 65 25 74 18

``` r
set.seed(42)
sample(1:100, size = 5)
```

    ## [1] 49 65 25 74 18

Both samples are identical because the same seed was set immediately
before each operation.

## 24.3 Avoid manual changes to analysed data

If a value must be corrected, document the correction in code.

``` r
laboratory_value <- c(12.4, 13.1, 131, 12.8)

# Correct a confirmed decimal-entry error documented in the laboratory log
laboratory_value[3] <- 13.1

laboratory_value
```

    ## [1] 12.4 13.1 13.1 12.8

Such corrections should be made only when supported by source
documentation. An unusual value should not be changed merely because it
looks inconvenient.

## 24.4 Test from a clean session

A script may appear to work because required objects remain in the
environment from earlier work.

Before sharing or publishing an analysis:

1.  restart R;
2.  open the project;
3.  run the complete script from the first line; and
4.  confirm that every required output is reproduced.

------------------------------------------------------------------------

# 25. R Markdown and GitHub Markdown

An R Markdown file usually has the extension `.Rmd`. It combines:

- explanatory text;
- headings and lists;
- mathematical notation;
- R code; and
- results generated by that code.

## 25.1 YAML header

The YAML header appears at the beginning of an R Markdown file.

``` yaml
---
title: "Chapter title"
output:
  github_document:
    toc: true
---
```

It controls the document title and output format.

## 25.2 R code chunks

An executable R chunk has this structure:

```` markdown

``` r
mean(c(10, 12, 14))
```

```
## [1] 12
```
````

Chunk names should be unique and descriptive.

## 25.3 Important chunk options

| Option            | Meaning                                    |
|-------------------|--------------------------------------------|
| `echo = TRUE`     | Show the R code                            |
| `echo = FALSE`    | Run the code but hide it                   |
| `eval = FALSE`    | Show the code but do not run it            |
| `include = FALSE` | Run the code but hide both code and output |
| `message = FALSE` | Hide package messages                      |
| `warning = FALSE` | Hide warnings in the rendered document     |
| `fig.cap`         | Add a figure caption                       |

Warnings should be hidden only after the analyst understands why they
occur.

## 25.4 Knitting the document

When the chapter is knitted:

1.  R starts with the instructions in the Rmd file;
2.  code chunks are executed in order;
3.  results and figures are generated;
4.  explanatory text and output are combined; and
5.  a Markdown file is created for GitHub.

If one chunk fails, later chunks may not run. Therefore, code order and
object creation matter.

------------------------------------------------------------------------

# 26. Integrated Case Study: Biological Sample Quality Control

Suppose a small sequencing study contains eight biological samples.

``` r
qc_data <- data.frame(
  sample_id = paste0("S", sprintf("%02d", 1:8)),
  group = rep(c("Control", "Treated"), each = 4),
  mapped_reads_million = c(42, 38, 19, 45, 51, 48, 44, 21),
  mapping_rate = c(0.92, 0.89, 0.61, 0.94, 0.95, 0.93, 0.90, 0.64),
  contamination = c(0.01, 0.02, 0.08, 0.01, 0.01, 0.02, 0.02, 0.09),
  stringsAsFactors = FALSE
)

print_html_table(
  qc_data,
  caption = "Hypothetical sequencing quality-control dataset."
)
```

<table class="chapter-table">

<caption>

Hypothetical sequencing quality-control dataset.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

group
</th>

<th style="text-align:right;">

mapped reads million
</th>

<th style="text-align:right;">

mapping rate
</th>

<th style="text-align:right;">

contamination
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

42
</td>

<td style="text-align:right;">

0.92
</td>

<td style="text-align:right;">

0.01
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

38
</td>

<td style="text-align:right;">

0.89
</td>

<td style="text-align:right;">

0.02
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

19
</td>

<td style="text-align:right;">

0.61
</td>

<td style="text-align:right;">

0.08
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

45
</td>

<td style="text-align:right;">

0.94
</td>

<td style="text-align:right;">

0.01
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

51
</td>

<td style="text-align:right;">

0.95
</td>

<td style="text-align:right;">

0.01
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

48
</td>

<td style="text-align:right;">

0.93
</td>

<td style="text-align:right;">

0.02
</td>

</tr>

<tr>

<td style="text-align:left;">

S07
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

44
</td>

<td style="text-align:right;">

0.90
</td>

<td style="text-align:right;">

0.02
</td>

</tr>

<tr>

<td style="text-align:left;">

S08
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

21
</td>

<td style="text-align:right;">

0.64
</td>

<td style="text-align:right;">

0.09
</td>

</tr>

</tbody>

</table>

## 26.1 Inspect the dataset

``` r
dim(qc_data)
```

    ## [1] 8 5

``` r
names(qc_data)
```

    ## [1] "sample_id"            "group"                "mapped_reads_million"
    ## [4] "mapping_rate"         "contamination"

``` r
str(qc_data)
```

    ## 'data.frame':    8 obs. of  5 variables:
    ##  $ sample_id           : chr  "S01" "S02" "S03" "S04" ...
    ##  $ group               : chr  "Control" "Control" "Control" "Control" ...
    ##  $ mapped_reads_million: num  42 38 19 45 51 48 44 21
    ##  $ mapping_rate        : num  0.92 0.89 0.61 0.94 0.95 0.93 0.9 0.64
    ##  $ contamination       : num  0.01 0.02 0.08 0.01 0.01 0.02 0.02 0.09

``` r
summary(qc_data)
```

    ##   sample_id            group           mapped_reads_million  mapping_rate   
    ##  Length:8           Length:8           Min.   :19.00        Min.   :0.6100  
    ##  Class :character   Class :character   1st Qu.:33.75        1st Qu.:0.8275  
    ##  Mode  :character   Mode  :character   Median :43.00        Median :0.9100  
    ##                                        Mean   :38.50        Mean   :0.8475  
    ##                                        3rd Qu.:45.75        3rd Qu.:0.9325  
    ##                                        Max.   :51.00        Max.   :0.9500  
    ##  contamination   
    ##  Min.   :0.0100  
    ##  1st Qu.:0.0100  
    ##  Median :0.0200  
    ##  Mean   :0.0325  
    ##  3rd Qu.:0.0350  
    ##  Max.   :0.0900

## 26.2 Define transparent quality-control rules

For this teaching example, suppose a sample passes if:

- mapping rate is at least 0.80; and
- contamination is no greater than 0.05.

``` r
qc_data$qc_pass <-
  qc_data$mapping_rate >= 0.80 &
  qc_data$contamination <= 0.05

print_html_table(
  qc_data,
  caption = "Quality-control dataset after applying the pass rules."
)
```

<table class="chapter-table">

<caption>

Quality-control dataset after applying the pass rules.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

group
</th>

<th style="text-align:right;">

mapped reads million
</th>

<th style="text-align:right;">

mapping rate
</th>

<th style="text-align:right;">

contamination
</th>

<th style="text-align:left;">

qc pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

42
</td>

<td style="text-align:right;">

0.92
</td>

<td style="text-align:right;">

0.01
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

38
</td>

<td style="text-align:right;">

0.89
</td>

<td style="text-align:right;">

0.02
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S03
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

19
</td>

<td style="text-align:right;">

0.61
</td>

<td style="text-align:right;">

0.08
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

45
</td>

<td style="text-align:right;">

0.94
</td>

<td style="text-align:right;">

0.01
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

51
</td>

<td style="text-align:right;">

0.95
</td>

<td style="text-align:right;">

0.01
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

48
</td>

<td style="text-align:right;">

0.93
</td>

<td style="text-align:right;">

0.02
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S07
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

44
</td>

<td style="text-align:right;">

0.90
</td>

<td style="text-align:right;">

0.02
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S08
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

21
</td>

<td style="text-align:right;">

0.64
</td>

<td style="text-align:right;">

0.09
</td>

<td style="text-align:left;">

FALSE
</td>

</tr>

</tbody>

</table>

These thresholds are hypothetical. Real thresholds must be justified
using the assay, protocol and study context.

## 26.3 Count passed and failed samples

``` r
print_html_table(
  table(qc_data$qc_pass),
  caption = "Numbers of samples passing and failing quality control."
)
```

<table class="chapter-table">

<caption>

Numbers of samples passing and failing quality control.
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

FALSE
</td>

<td style="text-align:right;">

2
</td>

</tr>

<tr>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:right;">

6
</td>

</tr>

</tbody>

</table>

``` r
qc_pass_proportions <- prop.table(table(qc_data$qc_pass))
print_html_table(
  data.frame(
    QC_status = names(qc_pass_proportions),
    Proportion = as.numeric(qc_pass_proportions)
  ),
  caption = "Proportions of samples passing and failing quality control."
)
```

<table class="chapter-table">

<caption>

Proportions of samples passing and failing quality control.
</caption>

<thead>

<tr>

<th style="text-align:left;">

QC status
</th>

<th style="text-align:right;">

Proportion
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

FALSE
</td>

<td style="text-align:right;">

0.25
</td>

</tr>

<tr>

<td style="text-align:left;">

TRUE
</td>

<td style="text-align:right;">

0.75
</td>

</tr>

</tbody>

</table>

## 26.4 Select samples that passed

``` r
qc_passed_data <- qc_data[qc_data$qc_pass, ]
print_html_table(
  qc_passed_data,
  caption = "Samples retained after quality control."
)
```

<table class="chapter-table">

<caption>

Samples retained after quality control.
</caption>

<thead>

<tr>

<th style="text-align:left;">

sample id
</th>

<th style="text-align:left;">

group
</th>

<th style="text-align:right;">

mapped reads million
</th>

<th style="text-align:right;">

mapping rate
</th>

<th style="text-align:right;">

contamination
</th>

<th style="text-align:left;">

qc pass
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

S01
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

42
</td>

<td style="text-align:right;">

0.92
</td>

<td style="text-align:right;">

0.01
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S02
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

38
</td>

<td style="text-align:right;">

0.89
</td>

<td style="text-align:right;">

0.02
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S04
</td>

<td style="text-align:left;">

Control
</td>

<td style="text-align:right;">

45
</td>

<td style="text-align:right;">

0.94
</td>

<td style="text-align:right;">

0.01
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S05
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

51
</td>

<td style="text-align:right;">

0.95
</td>

<td style="text-align:right;">

0.01
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S06
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

48
</td>

<td style="text-align:right;">

0.93
</td>

<td style="text-align:right;">

0.02
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

<tr>

<td style="text-align:left;">

S07
</td>

<td style="text-align:left;">

Treated
</td>

<td style="text-align:right;">

44
</td>

<td style="text-align:right;">

0.90
</td>

<td style="text-align:right;">

0.02
</td>

<td style="text-align:left;">

TRUE
</td>

</tr>

</tbody>

</table>

## 26.5 Visualize the two QC measurements

``` r
qc_colours <- ifelse(
  qc_data$qc_pass,
  "steelblue4",
  "firebrick3"
)

plot(
  x = qc_data$mapping_rate,
  y = qc_data$contamination,
  pch = 19,
  col = qc_colours,
  xlab = "Mapping rate",
  ylab = "Contamination proportion",
  main = "Sequencing sample quality control",
  xlim = c(0.55, 1.00),
  ylim = c(0.00, 0.10)
)

abline(v = 0.80, lty = 2, col = "gray40")
abline(h = 0.05, lty = 2, col = "gray40")

text(
  x = qc_data$mapping_rate,
  y = qc_data$contamination,
  labels = qc_data$sample_id,
  pos = 3,
  cex = 0.8
)

legend(
  "topright",
  legend = c("Pass", "Fail"),
  col = c("steelblue4", "firebrick3"),
  pch = 19,
  bty = "n"
)
```

<div class="figure" style="text-align: center">

<img src="Chapter_02_Essential_R_for_Biostatistics_files/figure-gfm/qc-case-study-plot-1.png" alt="Mapping rate and contamination for eight hypothetical sequencing samples. Dashed lines represent the teaching QC thresholds." width="85%" />
<p class="caption">

Mapping rate and contamination for eight hypothetical sequencing
samples. Dashed lines represent the teaching QC thresholds.
</p>

</div>

This case study combines objects, vectors, logical conditions, data
frames, subsetting, summaries and visualization.

------------------------------------------------------------------------

# 27. Common Beginner Mistakes

## Mistake 1: Using an object before creating it

Run code in a logical order from top to bottom.

## Mistake 2: Confusing `<-` and `==`

- `<-` assigns a value;
- `==` compares two values.

## Mistake 3: Ignoring uppercase and lowercase differences

`sample_data` and `Sample_Data` are different names.

## Mistake 4: Forgetting quotation marks around text

Use `"Control"`, not `Control`, unless `Control` is an existing object.

## Mistake 5: Comparing missing values with `== NA`

Use `is.na()`.

## Mistake 6: Assuming imported columns have correct data types

Use `str()` immediately after import.

## Mistake 7: Treating zero as automatically missing

Determine its meaning from the variable definition and scientific
context.

## Mistake 8: Installing packages every time a script runs

Install once and load when needed.

## Mistake 9: Using absolute paths throughout a project

Use a project and relative paths.

## Mistake 10: Clearing errors without reading them

The error message often contains the most useful clue.

## Mistake 11: Trusting an analysis that works only in an old environment

Restart R and run the complete script from the beginning.

------------------------------------------------------------------------

# 28. Chapter Summary

In this chapter, you learned that:

- R performs computations, while RStudio provides an interface for
  working with R;
- scripts preserve analyses more reliably than console-only work;
- objects store values and are usually created with `<-`;
- functions perform reusable operations using arguments;
- vectors are the foundation of many R operations;
- numeric, character and logical values behave differently;
- R may coerce mixed values to a common type;
- brackets and logical conditions select data;
- missing values must be detected with `is.na()`;
- factors represent categories;
- matrices store one data type in two dimensions;
- data frames store variables of different types in a table;
- data should be inspected before analysis;
- relative paths make projects portable;
- figures reveal patterns that summaries alone may hide;
- packages extend R;
- errors and warnings should be read, not ignored; and
- R Markdown combines code, results and explanation in a reproducible
  chapter.

------------------------------------------------------------------------

# 29. Check Your Understanding

## Question 1

Explain the difference between R and RStudio using the
engine-and-dashboard analogy.

## Question 2

What is the difference between `<-` and `==`?

## Question 3

Identify the type of each value:

1.  `42`
2.  `42L`
3.  `"42"`
4.  `TRUE`
5.  `NA`

## Question 4

Why does the following vector become character?

``` r
c(12.4, "missing", 13.1)
```

## Question 5

What is wrong with this expression?

``` r
glucose[glucose == NA]
```

## Question 6

Explain the meaning of each part of this expression:

``` r
sample_data[sample_data$qc_pass, ]
```

## Question 7

Why should a researcher use relative paths instead of repeatedly writing
a complete path such as `C:/Users/...`?

## Question 8

What is the difference between installing and loading a package?

------------------------------------------------------------------------

# 30. Practice with R

## Exercise 1: Create biological objects

Create objects containing:

1.  the gene name `APOE`;
2.  a sample size of 48;
3.  a mean expression value of 7.35; and
4.  a logical value showing that quality control passed.

Print all four objects.

## Exercise 2: Work with a vector

``` r
fragment_length <- c(185, 210, 195, 240, 225, 205)
```

Use R to:

1.  count the fragments;
2.  calculate the mean length;
3.  select the first and fourth values;
4.  select fragments longer than 210 base pairs; and
5.  convert the lengths to kilobases.

## Exercise 3: Work with missing data

``` r
protein_level <- c(4.2, NA, 5.1, 4.8, NA, 5.5)
```

Use R to:

1.  identify missing values;
2.  count missing values;
3.  calculate the mean using the available measurements; and
4.  select only non-missing measurements.

## Exercise 4: Create a factor

Create a factor from:

``` r
c("Low", "High", "Medium", "Low", "High")
```

Set the levels in the order `Low`, `Medium`, `High` and make it an
ordered factor.

## Exercise 5: Explore a data frame

``` r
patient_data <- data.frame(
  patient_id = paste0("P", 1:6),
  group = c("Control", "Control", "Control", "Treatment", "Treatment", "Treatment"),
  biomarker = c(5.2, 5.6, 5.4, 7.1, 6.8, 7.4),
  responder = c(FALSE, FALSE, TRUE, TRUE, TRUE, TRUE),
  stringsAsFactors = FALSE
)
```

Use R to:

1.  inspect its structure;
2.  report its dimensions;
3.  select the biomarker column;
4.  select treatment-group patients;
5.  count responders and non-responders;
6.  calculate mean biomarker level by group; and
7.  create a boxplot with individual observations.

## Exercise 6: Find and correct problems

Identify the error in each instruction.

``` r
Gene_name <- TP53

mean(c(5.2, 6.1, NA, 5.8))

sample_status[sample_status == NA]

clinical data <- read.csv("data/clinical.csv")

sample_data$Treatment == "Control"
```

------------------------------------------------------------------------

# 31. Mini-Project: Build and Explore a Small Biological Dataset

Create a data frame containing at least 10 biological samples and the
following variables:

- sample identifier;
- experimental group;
- tissue type;
- one numerical measurement;
- one binary quality-control outcome; and
- one variable containing at least one missing value.

Then:

1.  inspect the dataset with `str()`, `dim()`, `names()` and
    `summary()`;
2.  count samples in each experimental group;
3.  count missing values in each relevant variable;
4.  calculate the mean and median of the numerical measurement;
5.  calculate the mean separately for each group;
6.  select only samples that passed quality control;
7.  create one informative figure;
8.  write two sentences describing the observed data; and
9.  explain one limitation of the dataset.

Do not perform a formal hypothesis test yet.

------------------------------------------------------------------------

# 32. Glossary

| Term | Beginner-friendly meaning |
|----|----|
| R | A language and environment for statistical computing |
| RStudio | An interface used to write, run and organize R work |
| Console | The area where commands are executed immediately |
| Script | A saved text file containing R instructions |
| Environment | The objects currently stored in memory |
| Object | A named structure that stores information |
| Assignment | Storing a value in an object, usually with `<-` |
| Function | A reusable instruction that performs a task |
| Argument | Information supplied to a function |
| Vector | A one-dimensional collection of values of one basic type |
| Coercion | Conversion of values to a common data type |
| Indexing | Selecting values by position, name or condition |
| Factor | A structure used to represent categorical values |
| Matrix | A two-dimensional structure containing one basic data type |
| Data frame | A rectangular table whose columns may have different types |
| Missing value | An unavailable or unrecorded value represented by `NA` |
| Package | A collection of R functions, documentation and related resources |
| Relative path | A file location described relative to the project directory |
| R Markdown | A document that combines text, R code and generated results |
| Reproducibility | The ability to recreate an analysis from its inputs and code |

------------------------------------------------------------------------

# 33. References and Further Reading

1.  R Core Team. *R: A Language and Environment for Statistical
    Computing*. Vienna, Austria: R Foundation for Statistical Computing.
    Available from: <https://www.R-project.org/>

2.  Wickham H, Grolemund G. *R for Data Science: Import, Tidy,
    Transform, Visualize, and Model Data*. Sebastopol, CA: O’Reilly
    Media; 2017. Available from: <https://r4ds.had.co.nz/>

3.  Wickham H, Çetinkaya-Rundel M, Grolemund G. *R for Data Science:
    Import, Tidy, Transform, Visualize, and Model Data*. 2nd
    ed. Sebastopol, CA: O’Reilly Media; 2023. Available from:
    <https://r4ds.hadley.nz/>

4.  Grolemund G. *Hands-On Programming with R*. Sebastopol, CA: O’Reilly
    Media; 2014. Available from:
    <https://rstudio-education.github.io/hopr/>

5.  Wickham H. *Advanced R*. 2nd ed. Boca Raton, FL: CRC Press; 2019.
    Available from: <https://adv-r.hadley.nz/>

6.  Xie Y, Allaire JJ, Grolemund G. *R Markdown: The Definitive Guide*.
    Boca Raton, FL: CRC Press; 2018. Available from:
    <https://bookdown.org/yihui/rmarkdown/>

7.  Xie Y, Dervieux C, Riederer E. *R Markdown Cookbook*. Boca Raton,
    FL: CRC Press; 2020. Available from:
    <https://bookdown.org/yihui/rmarkdown-cookbook/>

8.  Gentleman R, Carey VJ, Bates DM, et al. Bioconductor: open software
    development for computational biology and bioinformatics. *Genome
    Biology*. 2004;5:R80. <doi:10.1186/gb-2004-5-10-r80>.

9.  Rosner B. *Fundamentals of Biostatistics*. 8th ed. Boston, MA:
    Cengage Learning; 2015.

------------------------------------------------------------------------

# 34. Reproducibility Information

The datasets in this chapter are hypothetical or simulated for teaching.
They should not be used to support biological or clinical conclusions.

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
