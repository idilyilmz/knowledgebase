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
The dot product of two vectors $$\mathbf{a}$$ and $$\mathbf{b}$$ is calculated as:

$$
\mathbf{a} \cdot \mathbf{b} = |\mathbf{a}| |\mathbf{b}| \cos(\theta)
$$

where $$ |\mathbf{a}| $$ and $$ |\mathbf{b}| $$ are the magnitudes (lengths) of vectors $$\mathbf{a}$$ and $$\mathbf{b}$$, and $$\theta$$ is the angle between them.

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
- For a 2D vector $$\mathbf{v} = (x, y)$$:
  
  $$
  |\mathbf{v}| = \sqrt{x^2 + y^2}
  $$

- For a 3D vector $$\mathbf{u} = (x, y, z)$$:
  
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

## 5. Multiplying Vectors by Matrices

In this worked example you will learn about:
- How to multiply vectors by matrices.

For this worked example you are assumed to be familiar with:
- What vectors are.
- What matrices are.

### General Rule

A vector in $$ \mathbb{R}^n $$ (with $$ n $$ elements) can be multiplied by a $$ m \times n $$ matrix. The multiplication is defined as:

$$
\mathbf{A} \cdot \mathbf{x} = 
\begin{pmatrix}
a_{11} & \cdots & a_{1n} \\
\vdots & \ddots & \vdots \\
a_{m1} & \cdots & a_{mn}
\end{pmatrix}
\cdot
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
=
\begin{pmatrix}
a_{11} \cdot x_1 + \ldots + a_{1n} \cdot x_n \\
\vdots \\
a_{m1} \cdot x_1 + \ldots + a_{mn} \cdot x_n
\end{pmatrix}
$$

### Examples

#### 1. Vector in $$ \mathbb{R}^2 $$ with a $$ 2 \times 2 $$ Matrix

Let 

$$
\mathbf{A} = 
\begin{pmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{pmatrix}
$$

and 

$$
\mathbf{x} = 
\begin{pmatrix}
x_1 \\
x_2
\end{pmatrix}
$$. 

The product is:

$$
\mathbf{A} \cdot \mathbf{x} = 
\begin{pmatrix}
a_{11} \cdot x_1 + a_{12} \cdot x_2 \\
a_{21} \cdot x_1 + a_{22} \cdot x_2
\end{pmatrix}
$$

For example, if 

$$
\mathbf{A} = 
\begin{pmatrix}
5 & 6 \\
7 & 8
\end{pmatrix}
$$

and 

$$\mathbf{x} = 
\begin{pmatrix}
10 \\
20
\end{pmatrix}$$
:

$$
\mathbf{A} \cdot \mathbf{x} = 
\begin{pmatrix}
5 \cdot 10 + 6 \cdot 20 \\
7 \cdot 10 + 8 \cdot 20
\end{pmatrix} = 
\begin{pmatrix}
170 \\
230
\end{pmatrix}
$$

#### 2. Vector in $$ \mathbb{R}^3 $$ with a $$ 2 \times 3 $$ Matrix

For 

$$
\mathbf{A} = 
\begin{pmatrix}
4 & 5 & 6 \\
7 & 8 & 9
\end{pmatrix}
$$

and 

$$\mathbf{x} = 
\begin{pmatrix}
10 \\
20 \\
30
\end{pmatrix}$$
:

$$
\mathbf{A} \cdot \mathbf{x} = 
\begin{pmatrix}
4 \cdot 10 + 5 \cdot 20 + 6 \cdot 30 \\
7 \cdot 10 + 8 \cdot 20 + 9 \cdot 30
\end{pmatrix} = 
\begin{pmatrix}
320 \\
500
\end{pmatrix}
$$

#### 3. Vector in $$ \mathbb{R}^2 $$ with a $$ 3 \times 2 $$ Matrix

If 
$$
\mathbf{A} = 
\begin{pmatrix}
1 & 2 \\
3 & 4 \\
5 & 6
\end{pmatrix}
$$

and 

$$\mathbf{x} = 
\begin{pmatrix}
10 \\
20
\end{pmatrix}$$

$$
\mathbf{A} \cdot \mathbf{x} = 
\begin{pmatrix}
1 \cdot 10 + 2 \cdot 20 \\
3 \cdot 10 + 4 \cdot 20 \\
5 \cdot 10 + 6 \cdot 20
\end{pmatrix} = 
\begin{pmatrix}
50 \\
110 \\
170
\end{pmatrix}
$$

### Conditions for Multiplication

A vector in $$ \mathbb{R}^n $$ cannot be multiplied by a $$ m \times k $$ matrix if $$ k \neq n $$.

#### Example of Undefined Multiplication

If 

$$
\mathbf{A} = 
\begin{pmatrix}
4 & 5 & 6 \\
7 & 8 & 9
\end{pmatrix}
$$

and 

$$
\mathbf{x} = 
\begin{pmatrix}
10 \\
20
\end{pmatrix}
$$, the product:

$$
\mathbf{A} \cdot \mathbf{x} = \text{Not defined}
$$

## 6. Matrix multiplication

### Matrix-Vector Product

To perform multiplication between a matrix $$ \mathbf{A} $$ and a vector $$ \mathbf{x} $$ (the matrix-vector product), the vector must be viewed as a column matrix. The product is defined when the number of columns in $$ \mathbf{A} $$ equals the number of rows in $$ \mathbf{x} $$.

If $$ \mathbf{A} $$ is an $$ m \times n $$ matrix, the vector $$ \mathbf{x} $$ is an $$ n \times 1 $$ column vector. The resulting vector $$ \mathbf{b} = \mathbf{A} \cdot \mathbf{x} $$ will be an $$ m \times 1 $$ column vector.

#### General Formula

$$
\mathbf{A} \cdot \mathbf{x} = \begin{pmatrix}
a_{11} & \cdots & a_{1n} \\
\vdots & \ddots & \vdots \\
a_{m1} & \cdots & a_{mn}
\end{pmatrix} \cdot \begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
$$

### Matrix-Matrix Product

The matrix-vector product is a special case of the matrix-matrix product. The product $$ \mathbf{A} \cdot \mathbf{B} $$ between matrices is defined when the number of columns in $$ \mathbf{A} $$ equals the number of rows in $$ \mathbf{B} $$.

If $$ \mathbf{A} $$ is an $$ m \times n $$ matrix and $$ \mathbf{B} $$ is an $$ n \times p $$ matrix, the product $$ \mathbf{C} = \mathbf{A} \cdot \mathbf{B} $$ is an $$ m \times p $$ matrix.

#### Calculation

Each column of $$ \mathbf{C} $$ is the matrix-vector product of $$ \mathbf{A} $$ with the respective column of $$ \mathbf{B} $$. The component in the $$ i $$-th row and $$ j $$-th column of $$ \mathbf{C} $$ is the dot product between the $$ i $$-th row of $$ \mathbf{A} $$ and the $$ j $$-th column of $$ \mathbf{B} $$.

### Examples

#### Example 1: Matrix-Vector Product

Let $$ \mathbf{A} = \begin{pmatrix} 1 & -3 \\ 2 & 3 \end{pmatrix} $$ and $$ \mathbf{x} = \begin{pmatrix} 2 \\ 5 \end{pmatrix} $$:
$$
\mathbf{A} \cdot \mathbf{x} = \begin{pmatrix} 1 \cdot 2 + (-3) \cdot 5 \\ 2 \cdot 2 + 3 \cdot 5 \end{pmatrix} = \begin{pmatrix} -13 \\ 19 \end{pmatrix}
$$

#### Example 2: Matrix-Matrix Product

Let $$ \mathbf{A} = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix} $$ and $$ \mathbf{B} = \begin{pmatrix} 0 & 1 \\ 1 & 2 \end{pmatrix} $$:
$$
\mathbf{A} \cdot \mathbf{B} = \begin{pmatrix} 1 \cdot 0 + 2 \cdot 1 \\ 3 \cdot 0 + 4 \cdot 1 \\ 1 \cdot 1 + 2 \cdot 2 \\ 3 \cdot 1 + 4 \cdot 2 \end{pmatrix} = \begin{pmatrix} 2 \\ 4 \\ 5 \\ 11 \end{pmatrix}
$$

## 7. Inverse Matrices - Conceptual Explanation

In this conceptual explanation you will learn about:
- Inverse matrices.

For this conceptual explanation you are assumed to be familiar with:
- Calculations with matrices.

### Inverse Matrix

An **inverse matrix** is a matrix that, when multiplied by its original matrix, yields the **identity matrix**. It is commonly denoted with a superscript $$-1$$.

#### Definition
For a square $$ n \times n $$ matrix $$ \mathbf{A} $$ and its inverse $$ \mathbf{A}^{-1} $$:

$$
\mathbf{A}^{-1} \mathbf{A} = \mathbf{I}_n
$$

where $$ \mathbf{I}_n $$ is the $$ n \times n $$ identity matrix.

##### Example
Let 

$$
\mathbf{A} = \begin{pmatrix}
1 & 1 & 2 \\
0 & 1 & 2 \\
0 & 1 & 3
\end{pmatrix}
$$

and 

$$
\mathbf{A}^{-1} = \begin{pmatrix}
1 & -1 & 0 \\
0 & 3 & -2 \\
0 & -1 & 1
\end{pmatrix}
$$

Then,

$$
\mathbf{A}^{-1} \mathbf{A} = \begin{pmatrix}
1 & -1 & 0 \\
0 & 3 & -2 \\
0 & -1 & 1
\end{pmatrix} \begin{pmatrix}
1 & 1 & 2 \\
0 & 1 & 2 \\
0 & 1 & 3
\end{pmatrix} = \begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix} = \mathbf{I}_3
$$

#### Conditions for Invertibility
Not all matrices have an inverse. A matrix is considered **invertible** if:

- An inverse matrix $$ \mathbf{A}^{-1} $$ exists.
- $$ \text{det}(\mathbf{A}) \neq 0 $$ (For a $$ 2 \times 2 $$ matrix, $$ \text{det}(a, b, c, d) = ad - bc $$).
- The rank of the $$ n \times n $$ matrix $$ \mathbf{A} $$ is $$ n $$.
- The columns of $$ \mathbf{A} $$ are linearly independent.
- The echelon form of $$ \mathbf{A} $$ is the identity matrix.

All these conditions are equivalent; if one holds true, all do.

