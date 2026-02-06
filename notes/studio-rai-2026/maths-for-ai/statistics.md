# Statistics

Everything you need to know for statistics !

## Mean

In this lesson you'll learn:

- How to read mathematical notation
- How to write the mean as a formula

### Mean Lesson Summary 

The **mean** is the average calculated from interval or ratio data. To find the mean, follow these steps:

1. **Add all values** together.
2. **Divide** the sum by the **number of values**.

To simplify, mathematicians use symbols: 

- **Σ** (σ) for sum 
- **n** for the number of values 
- **X̄** (X-bar) to denote the mean

Thus, the mean can be expressed in notation as:

$$
X̄ = Σx / n
$$

This notation makes the process of calculating the mean more concise.

## Median

In this lesson you will learn:
- What a measure of centre is.
- What outliers are.
- What the median is and how to find it.


### Median Lesson Summary

The **median** is a measure of center that represents the middle value of a data set, offering a more accurate depiction of central tendency in cases where outliers are present.

#### Importance of the Median

- While the **mean** provides a useful measure of central tendency, it can be distorted by outliers, such as a very high or low value that significantly affects the average.
- For instance, if a group has a mean age of **21.3 years**, but consists largely of children with one elderly participant, the mean may not accurately reflect the group’s actual demographic.

#### Steps to Calculate the Median

1. **Order** all values from low to high.
2. **Count** the total number of values.
3. **Divide** the count by **2** and round up to determine the position of the median.
4. **Locate** the middle value based on the position determined in step 3.

#### Worked Example

Given the dataset: **[4, 5, 16, 2, 4, 8, 25]**:

1. Ordered: **[2, 4, 4, 5, 8, 16, 25]**
2. Count: Total of **7 values**.
3. Position: **7 / 2 = 3.5** (round up to **4**).
4. Middle value: **5**.

Thus, the median is **5**.

#### Different Scenarios

For an even number of values, the median is the **mean** of the two middle values.

#### Summary

- The median effectively identifies the middle value in a dataset.
- It is particularly beneficial in the presence of outliers, ensuring a more representative measure of center.
- Calculating the median requires arranging the data, counting values, determining the middle position, and finding that middle value.

## Range

In this lesson you will learn:
- What the variation of your data means
- A first measure to you can use to express variation: the range

### Variation Lesson Summary

**Variation** refers to the extent to which values in a dataset differ from each other. Understanding variation is crucial, as it provides insight into the distribution of data points around the center.

#### Importance of Measuring Variation

- **Visual Assessment**: Judging variation by eye can be challenging, especially with large datasets (e.g., **10,000 values**).
- A numerical measure simplifies understanding the differences among values.

#### The Range as a Measure of Variation

The **range** is the first measure of variation, defined as the difference between the highest and lowest values in a dataset.

#### Formula for the Range

$$ 
\text{Range} = \text{Maximum} - \text{Minimum} 
$$

#### Worked Example

To find the range for **Group A**:

- **Maximum value**: **38**
- **Minimum value**: **26**

Applying the formula:

$$
\text{Range} = 38 - 26 = 12 
$$

Thus, the range is **12**.

#### Summary

- **Variation** indicates how much values differ from each other.
- The first measure discussed, the **range**, is calculated as the difference between the maximum and minimum values:

$$
\text{Range} = \text{Maximum} - \text{Minimum} 
$$ 

Understanding the range helps assess the spread of data effectively.

## Mode

In this lesson you will learn:
- What the Mode is
- How you find the Mode

Prerequisites:
- Measurement levels

### Mode Lesson Summary

In statistics, the **mode** is a measure of center that identifies the most frequently occurring value in a dataset. It helps in understanding which data point is most common, making it valuable for decision-making, such as in sales predictions.

#### Importance of the Mode

For instance, an ice cream seller may want to know which flavor generates the most sales. The simplest approach is to identify the flavor that has been sold the most—this value is known as the **mode**.

#### Steps to Find the Mode

1. **Count** the frequency of each value in the dataset.
2. The value with the highest frequency is the **mode**.
3. If two or more values share the highest frequency, there are multiple modes.

#### Worked Examples

1. **Ice Cream Sales**:
   - Values: Lemon (2), Strawberry (5), Banana (3), Chocolate (1), Pistachio (1).
   - The mode is **Strawberry**, as it occurs most frequently.

2. **Paint Shop Colors**:
   - Dataset: **[green, blue, red, green, green, red, blue, black, white, yellow, green, yellow, green, green, green]**.
   - The mode is **green**, which appears most often.

3. **Running Match Finish Times**:
   - Dataset: **[1:00:05, 1:00:04, 0:53:53, 0:51:32, 1:00:09, 0:51:39, 1:00:07, 1:00:10, 1:00:42, 1:00:48]**.
   - No time appears more than once; thus, there is **no mode** for this continuous data.

#### Conclusion on Mode's Applicability

The mode is particularly useful for **categorical data** because it identifies the most common category. However, it becomes less meaningful for **continuous data**, where values often do not repeat, making mode calculation less practical. This highlights that the mode may not be a convenient measure of center for continuous datasets.

## Quartiles

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

## Quartiles - Second Method

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

## Spread

In this lesson you will learn:
- What spread is
- Why spread is important

### Summary of Spread in Data

Understanding **spread** is crucial in addition to analyzing the center of data. Spread refers to how much data values differ from one another and from the measure of center. 

- **Example**: An average of **1,000** people travel by train hourly, with each wagon accommodating **100** people. If actual numbers vary significantly (e.g., doubling unexpectedly), relying solely on the average becomes inadequate for determining the number of required wagons.

- **Dotplots** can visualize spread, where each dot represents a certain number of people. Variations in dot height indicate different numbers traveling at different times. Consistent dots across hours suggest no variation; fluctuating dots indicate significant variation.

- To effectively allocate resources (like wagons), assessing spread is essential, as it helps identify peak travel times and necessary adjustments throughout the day. 

### Conclusion

Considering spread allows for a better understanding of data variability, making it vital for accurate planning and resource allocation. The more varied the data, the greater the spread, leading to more informed decision-making.

## Measures of Speed

In this lesson you will learn:
- Why you would want to measure spread
- That there are multiple measures of spread

We assume that you know the following terms:
- Spread
- Measure of centre

### Summary on Measures of Spread

When comparing groups, evaluating the **spread** of data is as important as assessing the **center**. 

#### Key Concepts

- **Measure of Center**: The best description is **“The point around which most of the data is concentrated.”**
- **Spread**: The most fitting description is **“How much the data values differ from each other.”**

#### Visualizing Spread

When inspecting the number of travelers at Gare de Lyon with a dotplot, you can determine the spread:

- If there's **little to no spread**, it indicates consistent travel numbers.
- If there's **a lot of spread**, it suggests significant variation in traveler numbers.

#### Criteria for Adding Rush-Wagons

To decide which route should receive rush-wagons (extra capacity), the best criterion is to look for the **highest measure of center**, as it indicates the time with the most travelers, especially during peak hours.

#### Measures of Spread

Typically, measures of spread include:

- **Range**
- **Mean Absolute Deviation (MAD)**
- **Variance**
- **Standard Deviation**

Among these, **median** is **not** a measure of spread.

#### Route Selection for Rush-Wagons

Given measures of spread for different routes:

- **Route 1**: 23.2
- **Route 2**: 15.6
- **Route 3**: 24.5
- **Route 4**: 19.2

You would choose **Route 3** for its highest measure of spread (24.5).

### Conclusion

Using numerical measures of spread allows for better decision-making when comparing multiple datasets, especially in dynamic contexts like train travel. Understanding these measures helps identify the variability within the data, allowing for more informed resource allocation.

## Variance (conceptual)

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

## Variance (calculate)

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

## Standard Deviation (conceptual)
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

## Standard Deviation

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

## Population and Sample

After this lesson you know:
- What the difference is between the sample and the population.
- What a representative sample means.
- How the characteristics about the population and sample are denoted.

### Summary of Population and Sample Concept

**Population**: The entire group of individuals that researchers wish to study. It can vary in size depending on the context, such as first-year medical students or all US citizens.

**Sample**: A smaller subset drawn from the population, used to make inferences about the larger group. It is crucial for the sample to be **representative**, reflecting the population's characteristics, such as age and education level.

#### Notation:
- **Population characteristics** are indicated by **Greek letters**:
  - **μ**: Population mean
  - **σ**: Population standard deviation
- **Sample characteristics** use **Roman letters**:
  - **x̄**: Sample mean
  - **s**: Sample standard deviation

#### Types of Statistics:
1. **Descriptive Statistics**: Occurs when the sample size equals the population size, allowing comprehensive conclusions (e.g., counting students in a class).
2. **Inferential Statistics**: Applies when the sample size is smaller than the population, requiring conclusions based on limited information.

This distinction between population and sample is fundamental in statistics.

## Box Plot

In this lesson you will learn:
- What variance is and why it is so important
- What a boxplot is and how to read it

We assume you completed the following lesson:
- Median
- Range
- Quartiles

### Summary of Box Plot Lesson Assignment

The assignment involves advising an ambulance service on the best route for delivering donor organs within 4 hours. Two routes are considered: the **highway** and the **city center**. 

---

#### Key Data Points

| Route         | Mean (hours) | Median (hours) |
|---------------|--------------|----------------|
| Highway       | **2.3**      | **1.7**        |
| City Center   | **2.8**      | **2.8**        |

Based on initial data, the highway seemed to be the better choice for a quicker delivery. However, complications arose when it was found that although the highway is generally faster, it can become significantly delayed during accidents. In contrast, the city center, while usually slower, allows for alternative routes, ensuring deliveries stay under the 4-hour limit.

---

#### Importance of Variation

The lesson emphasizes the importance of understanding both the **measure of center** (mean and median) and the **variation** (spread of data). This is crucial because relying solely on central measures can lead to flawed decisions, as illustrated by the unfortunate incident of late organ delivery.

---

#### Box Plot Overview

- **Middle Bar**: Represents the **median**.
- **Box**: Encloses the **middle 50%** of the data, defined by the first quartile (Q1) and third quartile (Q3).
- **Lines**: Indicate the minimum and maximum values.

---

#### Conclusion

A box plot effectively visualizes both the measure of center and the variation of data. Understanding the variation allows decision-makers, such as the ambulance service manager, to make more informed choices, avoiding potential disasters in critical situations.

## Histogram

In this lesson you will learn:
- What a histogram is and how to make one

We assume you know:
- What a continuous variable is
- What a bar graph is

### Concise Summary of Histogram vs. Bar Graph

When visualizing a large dataset of people's ages, using a bar graph can be challenging because age is measured on a **ratio scale**. Bar graphs are more suitable for **nominal/ordinal** data. 

---

#### Solutions

1. **Grouping Ages**: 
   - Divide ages manually into categories like young (0-18), adults (18-50), and seniors (50+).
  
2. **Using Classes/Bins**: 
   - Create fixed groups (e.g., 8 bins each covering a 4-year range).

---

#### Histograms

When using fixed groups, the chart becomes a **histogram**:
- **Characteristics**:
  - Data is divided into uniform groups.
  - Recommended group count is typically **8-10**.
  - Bars are adjacent, indicating continuous data connection.

---

#### Conclusion

For interval/ratio data, a histogram is preferred, allowing for clearer representation of age distribution compared to a bar graph.