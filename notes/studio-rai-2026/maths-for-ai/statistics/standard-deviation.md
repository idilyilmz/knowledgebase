# Module 1: Statistics

Everything you need to know for statistics !

## 11. Standard Deviation (conceptual)
In this lesson you will learn:
- What a standard deviation is
- Why we use the standard deviation as the standard measure of spread

We assume that you know the following concepts:
- Measurement level
- Spread
- Measures of spread
- Variance

### Summary on Standard Deviation

The **standard deviation** is a key measure of spread, addressing some of the drawbacks of variance. 

#### Key Concepts

- **Variance**: Best described as **“Average squared deviations.”**
- **Disadvantage of Variance**: Its unit is squared (e.g., **sec²**), making interpretation difficult.

#### Transition to Standard Deviation

- To convert variance back to the original unit, take the **square root**.
- The standard deviation is represented by the symbol \( \σ \) and is defined as the mean squared deviation in the units of the original variable.

#### Advantages of Standard Deviation

- Mathematically manageable for optimization.
- Emphasizes extreme values better than mean absolute deviation.
- Its unit matches that of the original variable, enhancing interpretability.

#### Application Example

When assessing running times, Anna has the highest variance of **5.16**, indicating the largest spread among her peers.

### Conclusion

The standard deviation is considered the standard measure of spread due to its practicality and interpretability in statistical analysis.

## 12. Standard Deviation

In this lesson you will learn:
- The standard way to measure variation.
- What the Sum of Squares, Variance and Standard Deviation are.
- A handy way to calculate the standard deviation.

We expect that you are able to:
- Calculate a mean.
- Square a number.

### Summary on Standard Deviation

**Standard Deviation** is the primary measure of variation, reflecting the average distance of data points from the mean.

#### Key Formulas

- **Population Standard Deviation**: 

$$
\sigma = \frac{\sum_{i=1}^{N} (x_i - \mu)^2}{N}
$$
  
- **Sample Standard Deviation**: 

$$
s = \frac{\sum_{i=1}^{n} (x_i - \bar{x})^2}{n - 1}
$$

Where \( \σ \) and \( \mu \) denote the population standard deviation and mean, respectively, and \( s \) and \( \bar{x} \) denote the sample standard deviation and mean, respectively.

#### Steps to Calculate Standard Deviation

1. **Calculate Deviation Scores**: Find the difference between each value and the mean.
  
2. **Calculate Sum of Squares (SS)**: Square each deviation and sum them.
  
3. **Calculate Variance**: Divide the sum of squares by the number of observations (using \( n - 1 \) for samples).
  
4. **Calculate Standard Deviation**: Take the square root of the variance.

#### Conclusion

Standard deviation provides insights into the variation within a dataset. A larger standard deviation indicates greater variation in data points. The calculation process involves four clear steps to transform deviations into a usable measure of spread.

#### Tip:

- When the number of values increases by twofold, but the sum of squares remains the same: the variance is divided by two.
- If the standard deviation increases by twofold, the variance also increases twofold.
- The standard deviation is **not** a measure of association within the population distribution.
