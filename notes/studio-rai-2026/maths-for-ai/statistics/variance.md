# Module 1: Statistics

Everything you need to know for statistics !

## 9. Variance (conceptual)

In this lesson you will learn:
- What variance is
- Why we use variance as a measure of spread

We assume that you know the following concepts:
- Spread
- Mean absolute deviation

### Summary on Variance as a Measure of Spread

**Variance** is a statistical measure that quantifies how far individual data points in a dataset are from the mean, emphasizing the significance of extreme values through squaring deviations.

#### Key Concepts

- **Mean Absolute Deviation**: Best described as **“Average absolute deviation.”**
- **Disadvantages of Mean Absolute Deviation**:
  - It does not emphasize extreme values enough.
  - It is mathematically difficult to optimize.

#### Transition to Variance

- Squaring deviations eliminates the negative sign and increases the impact of extreme values, making the variance more reflective of their significance.
- **Variance** is defined as the **mean squared deviation** of values relative to their mean and is denoted by \( \σ^2 \).

#### Comparison of Variance

When analyzing variance for running times:
- **Jasper**: 22.5
- **Joey**: 10.6
- **Anna**: 26.6
- **Kevin**: 8.4
- **Michelle**: 19.7

**Anna** has the largest spread based on variance (26.6).

#### Flaw of Variance

A key drawback of variance is that its unit is squared (e.g., squared minutes), making it challenging to interpret compared to the original data units.

### Conclusion

Variance effectively measures spread by emphasizing extreme values, but interpreting its results can be complicated due to its squared units. High variance indicates a greater spread in the dataset.

## 10. Variance (calculate)

In this lesson you will learn:
- How to calculate the variance

We assume that you already know:
- What spread is
- What variance is
- How to calculate an average
- How to square numbers

### Summary on Calculating Variance

**Variance** measures the spread of data and is defined as **“The mean of the squared deviations.”** It is represented by the symbol \( \σ^2 \).

#### Steps to Calculate Variance

1. **Calculate the Mean**:
   - For a dataset (e.g., bowling scores), find the average score.
  
2. **Calculate Deviations**:
   - Subtract the mean from each individual score to find the distance from the mean.

3. **Square the Deviations**:
   - Eliminate negative signs by squaring each deviation.

4. **Calculate the Sum of Squared Deviations**:
   - Add all squared deviations together.

5. **Calculate the Variance**:
   - Divide the sum of squared deviations by the number of observations.

#### Conclusion

The variance is derived through systematic steps involving the mean and squared deviations, providing a quantitative measure of data spread.
