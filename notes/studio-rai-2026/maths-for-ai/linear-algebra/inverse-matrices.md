# Module 2: Linear Algebra

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

## 8. Find the Inverse off a 2x2 Matrix
In this worked example you will learn about:
- How to find the inverse of a 2x2 matrix.

For this worked example you are assumed to be familiar with:
- Inverse matrices.

### Finding the Inverse of a $$ 2 \times 2 $$ Matrix

To find the inverse 

$$
\mathbf{A}^{-1}
$$

of the matrix 

$$
\mathbf{A} = \begin{pmatrix}
30 & 32 \\
35 & 38
\end{pmatrix}
$$

#### Step 1: Check Invertibility

It’s advisable to check if the matrix is invertible before calculations. Conditions for invertibility include:

An inverse matrix 

$$ 
\mathbf{A}^{-1} 
$$ 
exists.

$$ 
\text{det}(\mathbf{A}) \neq 0 
$$

(For a 

$$
2 \times 2
$$

matrix: 
$$
\text{det}(a, b, c, d) = ad - bc
$$
).

The matrix's rank is 
$$ n $$

The columns are linearly independent.

The echelon form is the identity matrix.

#### Step 2: Apply the Inverse Formula

For a 
$$
2 \times 2 
$$
matrix 

$$
\mathbf{A} = \begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$

the inverse is given by:

$$
\mathbf{A}^{-1} = \frac{1}{\text{det}(\mathbf{A})} \begin{pmatrix}
d & -b \\
-c & a
\end{pmatrix}
$$

#### Step 3: Calculate the Inverse

For the given matrix 

$$
\mathbf{A}
$$:

1. Calculate the determinant:

$$
\text{det}(\mathbf{A}) = 30 \cdot 38 - 32 \cdot 35 = 20
$$

2. Substitute into the inverse formula:

$$
\mathbf{A}^{-1} = \frac{1}{20} \begin{pmatrix}
38 & -32 \\
-35 & 30
\end{pmatrix} = \begin{pmatrix}
1.9 & -1.6 \\
-1.75 & 1.5
\end{pmatrix}
$$

#### Step 4: Verify the Solution

To confirm the accuracy, multiply 

$$
\mathbf{A}^{-1} 
$$ 

by 

$$ 
\mathbf{A} 
$$

$$
\begin{pmatrix}
1.9 & -1.6 \\
-1.75 & 1.5
\end{pmatrix} \begin{pmatrix}
30 & 32 \\
35 & 38
\end{pmatrix} = \begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix} = \mathbf{I}_2
$$

This confirms that the solution is correct.
