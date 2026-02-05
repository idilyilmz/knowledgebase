# Statistics

Everything you need to know for statistics !

## Mean

In this lesson you'll learn:

- How to read mathematical notation
- How to write the mean as a formula

The **mean** is the average calculated from interval or ratio data. To find the mean, follow these steps:

1. **Add all values** together.
2. **Divide** the sum by the **number of values**.

To simplify, mathematicians use symbols: 

- **Σ** (Sigma) for sum 
- **n** for the number of values 
- **X̄** (X-bar) to denote the mean

Thus, the mean can be expressed in notation as:

$$X̄ = Σx / n$$

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