# Module 2: Linear Algebra

## 1. Unit Vector

### Summary of Unit Vector Module

A **unit vector** is a vector with a length of **1** in a normed vector space. It is typically represented by a lowercase letter with a circumflex, such as **$$ \hat{v} $$**. The term **normalized vector** is synonymous with unit vector.

#### Normalization
To find the **normalized vector** $$ \hat{u} $$ of a non-zero vector $$ u $$, you divide each component of $$ u $$ by its norm (or length), represented as $$ ||u|| $$

$$ 
\hat{u} = \frac{u}{||u||} = \left(\frac{u_1}{||u||}, \frac{u_2}{||u||}, \ldots, \frac{u_n}{||u||}\right)
$$

#### Applications
Unit vectors are crucial for:
- Representing directions, including normal directions.
- Forming the basis of a vector space, where any vector in that space can be expressed as a linear combination of unit vectors. 

Unit vectors aid in simplifying calculations and maintaining directional consistency in vector analysis.

## 2. Dot product

### Definition
The **dot product**, also known as the **scalar product**, combines two vectors to produce a single scalar value. It measures how much two vectors point in the same direction.

### Formula
The dot product of two vectors \(\mathbf{a}\) and \(\mathbf{b}\) is calculated as:

$$
\mathbf{a} \cdot \mathbf{b} = |\mathbf{a}| |\mathbf{b}| \cos(\theta)
$$

where \( |\mathbf{a}| \) and \( |\mathbf{b}| \) are the magnitudes (lengths) of vectors \(\mathbf{a}\) and \(\mathbf{b}\), and \(\theta\) is the angle between them.

If the components of the vectors are known (e.g., for 2D vectors $$\mathbf{a} = (a_1, a_2)$$ and $$\mathbf{b} = (b_1, b_2)$$ the dot product can be expressed as:

$$
\mathbf{a} \cdot \mathbf{b} = a_1 b_1 + a_2 b_2
$$

### Interpretation
- **Positive Dot Product**: Vectors are generally pointing in the same direction.
- **Zero Dot Product**: Vectors are perpendicular (orthogonal) to each other.
- **Negative Dot Product**: Vectors are generally pointing in opposite directions.

### Example
For the vectors $$\mathbf{a} = (2, 3)$$ and $$\mathbf{b} = (-3, 5)$$:

$$
\mathbf{a} \cdot \mathbf{b} = 2 \cdot (-3) + 3 \cdot 5 = 9
$$

## 3. Length of a vector

### Definition
The **length** (or magnitude) of a vector is calculated by finding the square root of the sum of the squares of its components. 

### Formulas
- For a 2D vector \(\mathbf{v} = (x, y)\):
  
  $$
  |\mathbf{v}| = \sqrt{x^2 + y^2}
  $$

- For a 3D vector \(\mathbf{u} = (x, y, z)\):
  
  $$
  |\mathbf{u}| = \sqrt{x^2 + y^2 + z^2}
  $$

This is derived from the Pythagorean theorem.

### Steps to Calculate Vector Length
1. **Square each component** of the vector.
2. **Add the squared values** together.
3. **Take the square root** of the sum to find the vector's length.

### Examples
- **2D Vector**: For $$\mathbf{a} = (3, 4)$$:
  $$
  |\mathbf{a}| = \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = \sqrt{25} = 5
  $$

- **3D Vector**: For $$\mathbf{u} = (2, 4, -1)$$:
  $$
  |\mathbf{u}| = \sqrt{2^2 + 4^2 + (-1)^2} = \sqrt{4 + 16 + 1} = \sqrt{21}
  $$

### Notation
The length (or magnitude) of a vector $$\mathbf{v}$$ is often denoted by $$ |\mathbf{v}| $$.

## 4. Calculations with Vectors

In this worked example you will learn about:
- Addition of vectors.
- Scalar multiplication of vectors.

For this worked example you are assumed to be familiar with:
- What vectors are.

### Vector Calculations

#### Addition
Vectors are added **componentwise**. For vectors $$\mathbf{a} = (a_1, a_2, \ldots, a_n)$$ and $$\mathbf{b} = (b_1, b_2, \ldots, b_n)$$:

$$
\mathbf{a} + \mathbf{b} = (a_1 + b_1, a_2 + b_2, \ldots, a_n + b_n)
$$

##### Example
For $$\mathbf{a} = (1, 2, 3)$$ and $$\mathbf{b} = (4, 5, 6)$$:

$$
\mathbf{a} + \mathbf{b} = (1 + 4, 2 + 5, 3 + 6) = (5, 7, 9)
$$

**Note**: Vectors of different sizes cannot be added:

$$
\mathbf{a} + \mathbf{b} \quad \text{is not defined if} \quad n \neq m
$$

##### Example
For $$\mathbf{a} = (1, 2, 3)$$ and $$\mathbf{b} = (4, 5, 6, 7)$$:

$$
\mathbf{a} + \mathbf{b} \quad \text{is not defined}
$$

#### Scalar Multiplication
Vectors can be multiplied by a **scalar** (a real number) componentwise. For a scalar $$\lambda$$ and vector $$\mathbf{a} = (a_1, a_2, \ldots, a_n)$$:

$$
\lambda \cdot \mathbf{a} = (\lambda \cdot a_1, \lambda \cdot a_2, \ldots, \lambda \cdot a_n)
$$

##### Example
For $$\lambda = 3$$ and $$\mathbf{a} = (1, 2, 3)$$:

$$
3 \cdot \mathbf{a} = (3 \cdot 1, 3 \cdot 2, 3 \cdot 3) = (3, 6, 9)
$$
