# Module 2: Linear Algebra

## 6. Matrix multiplication

### Matrix-Vector Product

To perform multiplication between a matrix 

$$ \mathbf{A} $$ 

and a vector 

$$ \mathbf{x} $$ 

(the matrix-vector product), the vector must be viewed as a column matrix. The product is defined when the number of columns in 

$$ \mathbf{A} $$

equals the number of rows in 
 
$$ \mathbf{x} $$

If 

$$ \mathbf{A} $$

is an 
 
$$ m \times n $$

matrix, the vector 

$$ \mathbf{x} $$

is an 

$$ n \times 1 $$

column vector. The resulting vector 

$$ \mathbf{b} = \mathbf{A} \cdot \mathbf{x} $$

will be an 

$$ m \times 1 $$

column vector.

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

The matrix-vector product is a special case of the matrix-matrix product. The product 

$$ \mathbf{A} \cdot \mathbf{B} $$

between matrices is defined when the number of columns in 

$$ \mathbf{A} $$

equals the number of rows in

$$ \mathbf{B} $$

.

If 

$$ \mathbf{A} $$ 

is an

$$ m \times n $$

matrix and

$$ \mathbf{B} $$

is an 

$$ n \times p $$

matrix, the product 

$$\mathbf{C} = \mathbf{A} \cdot \mathbf{B} $$ 

is an 

$$ m \times p $$ 

matrix.

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
