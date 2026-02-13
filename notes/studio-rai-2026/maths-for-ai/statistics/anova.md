# Module 1: Statistics

## 18. ANOVA

In this lesson you'll learn:
- What error inflation is.
- What an ANOVA is.
- What you can use an ANOVA for.
- How an ANOVA works.

We assume that you know the following concepts:
- Type-I and Type-II errors.

### Summary of ANOVA and Error Rate Inflation

The minister of agriculture has requested an analysis of crop yields from three types of grain (A, B, and C) grown by seven farmers. The objective is to determine if there are significant differences in yield among these types.

#### Key Data

- **Mean Yields**:
  - Type A: **125.9**
  - Type B: **130.6**
  - Type C: **124.3**

#### Error Rate Inflation

When comparing means using multiple tests, such as t-tests, the risk of a **Type I error** (incorrectly rejecting a true null hypothesis) increases. Performing three separate tests can inflate this error rate from **5%** to **14%**. This phenomenon is known as **error rate inflation** or **multiple comparison error**.

#### Solution: ANOVA

In response to the error rate inflation issue, **ANOVA (ANalysis Of VAriance)** was developed by Fisher in the 1920s. It helps to determine if there are differences among group means by analyzing their variances.

##### How ANOVA Works

1. **Total Variation vs. Within-Group Variation**: 
   - If group means are similar, the variances will also be similar.
   - A large difference in means results in greater total variance compared to within-group variance.

2. **Calculating Variance**: 
   - Squaring the differences between the data points and their group mean prevents cancellation of positive and negative values.
   - Two key calculations:
     - The distance squared between the grand mean and each group mean.
     - The distance squared between each data point and its respective group mean.

3. **Deriving ANOVA Results**:
   - Compare the mean squared differences between groups and within groups.
   - A significant difference is indicated when the variance between groups is substantially larger than the variance within groups.

#### Conclusion

ANOVA effectively assesses differences between multiple group means without inflating the error rate. While it indicates that at least two means differ significantly, it does not specify which means differ from one another. Future lessons will cover the mathematical execution of ANOVA and how to use SPSS for these calculations.

#### Tips
- What does the abbreviation ANOVA mean?: **Analysis of Variance**
- An ANOVA can **not** be used to find out which of the groups has a higher mean.
- What is the null hypothesis for an ANOVA test?: **H0 : μ1 = μ2 = μ3**
- What is the measurement level of the dependent variable in an ANOVA?: **Interval**
- Where do you use ANOVA for? **to compare means**
- Which statistical test do you use in an ANOVA? **F-Test**

## 19. ANOVA Calculations

In this lesson you will learn:
- What steps to take to perform an ANOVA.
- What calculations you should when performing an ANOVA.

We assume you have followed the following lesson:
- ANOVA.

### Concise summary — ANOVA calculations (by hand)

**Goal:**
ANOVA tests whether **group means differ** by comparing variation **between groups** vs **within groups** using an **F-test**.

If

$$
F_{test} > F_{critical}
$$

→ at least one group mean is significantly different.

### Core idea

Total variation is split into two parts:

1. **Between groups** → difference of each group mean from the grand mean
2. **Within groups** → difference of each value from its own group mean

ANOVA checks whether between-group variation is large relative to within-group variation.

### Steps to calculate ANOVA test value

#### 1. Calculate group means

Mean of each group separately.

#### 2. Calculate the grand mean

Mean of **all observations combined**
(If group sizes equal → average the group means)

#### 3. Calculate sums of squares

**Between groups (SSB)**

$$
SSB = \sum n(\bar{x}*i - \bar{x}*{grand})^2
$$

Measures how far group means are from the overall mean.

**Within groups (SSW)**

$$
SSW = \sum (x_{ij} - \bar{x}_i)^2
$$

Measures spread inside each group.

#### 4. Degrees of freedom

$$
df_1 = c - 1 \quad (\text{between groups})
$$

$$
df_2 = N - c \quad (\text{within groups})
$$

Where

* (c) = number of groups
* (N) = total observations

#### 5. Mean squares

$$
MSB = \frac{SSB}{df_1}
$$

$$
MSW = \frac{SSW}{df_2}
$$

These are average variances.

#### 6. F-value

$$
F = \frac{MSB}{MSW}
$$

* MSB is always on top
* F ≥ 1 → one-sided test

### Interpretation

* **Large F** → groups differ more than expected by chance → significant
* **Small F** → differences likely random

### Key terms

* **SSB**: variance between groups
* **SSW**: variance within groups
* **MSB**: mean variance between
* **MSW**: mean variance within
* **F-test**: compares MSB and MSW

### Final takeaway

ANOVA determines whether group means differ by comparing **signal (between-group variation)** to **noise (within-group variation)**.
If the signal is big enough → at least one mean is different.
