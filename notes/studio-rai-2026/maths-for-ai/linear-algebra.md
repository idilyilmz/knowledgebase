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
