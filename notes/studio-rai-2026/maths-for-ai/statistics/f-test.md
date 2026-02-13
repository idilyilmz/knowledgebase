# Module 1: Statistics

Everything you need to know for statistics !

## 17. F-Test

In this lesson you will learn:
- What an F-distribution is.
- What an F-test is.
- How to perform an F-test and how to draw conclusions from it.

We assume you know:
- What the variance is and how to calculate it.

### Summary of F-Test for Variance Differences

The **F-test** is a statistical method used to compare the variances of two groups, allowing researchers to determine if there is a significant difference between them.

#### Key Concepts

- **Historical Context**: The F-test originated when statisticians focused on variances instead of standard deviations.
- **Variance Calculation**:
  1. Calculate the difference between each value and the mean.
  2. Square these differences and sum them.
  3. Divide this sum by the total number of values to find the variance.
- The **F-value** is computed by dividing the variance of one group by the variance of the other:
  
$$
F = \frac{\text{variance A}}{\text{variance B}}
$$

#### F-Distribution

The F-distribution is utilized to understand the variability of F-values derived from multiple samples from the same population. 

#### Example Application: Machine Variances

**Scenario**: Assessing the variances of two machines' cylinder production.

1. **Hypotheses**:
   - Null Hypothesis (\(H_0\)): Variances are equal (\(\sigma_1^2 = \sigma_2^2\)).
   - Alternative Hypothesis (\(H_a\)): Variances are not equal (\(\sigma_1^2 \neq \sigma_2^2\)).
   
2. **Sample Data**:
   - Machine A: Standard deviation = 6 mm
   - Machine B: Standard deviation = 4 mm

3. **Steps**:
   - Critical F-value (5% significance): 2.27
   - Calculate F-value: 

$$
F = \frac{6^2}{4^2} = \frac{36}{16} = 2.25
$$

4. **Conclusion**: Since 2.25 < 2.27, the difference is not statistically significant; thus, we fail to reject \(H_0\).

#### Further Example: Reaction Times

For a new scenario investigating reaction times of two groups:
- Group 1: 11 people, standard deviation = 5 ms.
- Group 2: 7 people, standard deviation = 4 ms.

1. **Null Hypothesis**: \(H_0: \sigma_1^2 = \sigma_2^2\)
2. **Test Selection**: An F-test is appropriate for comparing variances.
3. **Significance Level**: 10% (with critical F-values of 0.180 and 4.060).
4. The resulting F-value would be calculated similarly, and implications drawn based on comparisons with critical values.

#### Conclusion

By conducting an F-test, researchers can effectively evaluate whether two samples likely originate from the same population or different populations based on their variances. The results offer insights into the significance of their findings regarding variance differences.

#### Tips

- The F-value is always positive
- The measurement level of independent variable in an F-tets is **nominal**
- The measurement level of the dependent variable of an F-test is **ratio**
- You use the F-test to determine a difference between **variances**
- You use the F-test for: **difference between samples**
