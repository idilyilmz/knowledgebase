# Module 1: Statistics

Everything you need to know for statistics !

## 5. Quartiles

In this lesson you will learn:
- What quartiles are and how to find them
- What the Inter Quartile Range is and how to calculate it


We assume you know how to find:
- The range
- The median

### Quartiles and Interquartile Range (IQR) Lesson Summary

**Variation** or **spread** indicates how much the values in a dataset differ from one another. This lesson focuses on quartiles, which provide a robust measure of variation, especially in the presence of outliers.

#### Understanding Quartiles

Quartiles split your dataset into four equal parts, with each part containing **25%** of the data. For many datasets, relying solely on the range (the difference between the maximum and minimum values) can be misleading, especially when outliers are present.

#### Steps to Find the Quartiles

1. **Order** all values in the dataset from lowest to highest.
2. **Find the median** (also known as the second quartile or **Q2**).
3. **Determine the first quartile (Q1)** by finding the median of the lower half of the data (including Q2).
4. **Determine the third quartile (Q3)** by finding the median of the upper half of the data (including Q2).

#### Worked Example: Odd Number of Values

Given an unordered dataset, apply the above steps:

1. **Ordered dataset**: [1, 2, 4, 5, 6, 8, 9, 105]
2. **Median (Q2)**: **6**
3. **First quartile (Q1)**: Median of [1, 2, 4, 5, 6] → **4**
4. **Third quartile (Q3)**: Median of [6, 8, 9, 105] → **8**

**Conclusion**: Quartiles are \( Q1 = 4 \), \( Q2 = 6 \), and \( Q3 = 8 \).

#### Worked Example: Even Number of Values

For an even number of values, quartiles fall between values. Use the following approach:

1. **Ordered dataset**: [1, 2, 4, 5, 6, 8]
2. **Median (Q2)**: \( \frac{6 + 8}{2} = 7 \)
3. **First quartile (Q1)**: Median of [1, 2, 4, 5, 6] → **4.5**
4. **Third quartile (Q3)**: Median of [8, 9, 105] → \( \frac{8 + 9}{2} = 8.5 \)

**Conclusion**: Quartiles are \( Q1 = 4.5 \), \( Q2 = 7 \), and \( Q3 = 8.5 \).

#### Interquartile Range (IQR)

The **Interquartile Range (IQR)** measures the spread of the middle **50%** of the data:

$$
\text{IQR} = Q3 - Q1 
$$

#### Worked Example of IQR

Given \( Q1 = 4.5 \) and \( Q3 = 8.5 \):

$$ 
\text{IQR} = 8.5 - 4.5 = 4 
$$

#### Summary

- Quartiles split data into four equal parts, providing valuable insight into data distribution.
- The IQR can be a more reliable measure of variation than the range, especially in the presence of outliers, as it reflects the distance between \( Q1 \) and \( Q3 \) and focuses on the middle 50% of the data.
- Quartiles can be calculated using the median to find the values that partition the dataset effectively.

## 6. Quartiles - Second Method

In this lesson you will learn:
- What quartiles are and how to find them
- What the Inter Quartile Range is and how to calculate it

We assume you know how to find:
- The range
- The median

*Note*:  This lesson is an adapted copy of the default lesson on quartiles. In contrast to the default lesson on quartiles, this lesson computes the quartiles without including the median. 

### Key Differences in Summary

- The explanation emphasizes that the **range** is not a reliable measure of variation due to the influence of outliers, specifically referencing the outlier **105**.
- It introduces the concept of dividing data into **quartiles** for better insight into distribution.
- The steps for finding quartiles clarify that the median is referred to as \(Q_2\), and it states explicitly that the calculation method differs for odd and even datasets.
- In the worked example with odd numbers of values, it specifies that the median of the lower half does not include the overall median in its calculation.
- The calculation of \(Q_1\) now reflects the median of the values **without including the overall median** for the first half, yielding \(Q_1 = 3\).
- In the even-numbered example, it indicates that quartiles fall between two values and that the average of these two values must be calculated.
- The Interquartile Range (IQR) is introduced as the range between \(Q_1\) and \(Q_3\), providing a better spread measure, calculated as \(\text{IQR} = Q_3 - Q_1\).

### Conclusion of Key Differences

The lesson emphasizes the importance of quartiles for assessing data variation and specifies how to calculate them based on whether the dataset has an odd or even number of values. It also introduces the IQR as a more robust measure of spread compared to the range.
