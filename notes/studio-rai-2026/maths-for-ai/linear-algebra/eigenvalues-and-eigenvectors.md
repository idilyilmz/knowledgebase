# Module 2: Linear Algebra

## 9. Eigenvalues and eigenvectors

### Definitions
- **Eigenvector**: A non-zero vector that does not change direction when a transformation is applied (it may change length). 
- **Eigenvalue**: The scalar that represents the change in length of the eigenvector, typically denoted by $$ \lambda $$.

The term "eigen" is German for "own" or "typical". For a square matrix $$ \mathbf{A} $$, scalar $$ \lambda $$, and non-zero vector $$ \mathbf{v} $$, they satisfy the equation:

$$
\mathbf{A}\mathbf{v} = \lambda \mathbf{v}
$$

Here, $$ \lambda $$ is the eigenvalue, and $$ \mathbf{v} $$ is the eigenvector.

### Example 1: Calculating Eigenvalues
Given the matrix

$$
\mathbf{A} = \begin{pmatrix}
1 & 2 \\
2 & 1
\end{pmatrix}
$$

To find the eigenvalues, solve:

$$
\text{Det}(\mathbf{A} - \lambda \mathbf{I}) = 0
$$

where 

$$
\mathbf{I} = \begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}
$$

This leads to:

$$
\text{Det}\left(\begin{pmatrix}
1-\lambda & 2 \\
2 & 1-\lambda
\end{pmatrix}\right) = 0
$$

Calculating the determinant:

$$
(1-\lambda)^2 - (2)(2) = 0
$$

This simplifies to:

$$
\lambda^2 - 2\lambda - 3 = 0
$$

Factoring gives:

$$
(\lambda - 3)(\lambda + 1) = 0
$$

Thus, the eigenvalues are:

$$
\lambda = 3 \quad \text{or} \quad \lambda = -1
$$

### Example 2: Calculating Eigenvectors
Using the eigenvalue $$ \lambda = 3 $$:

$$
\mathbf{A}\mathbf{v} = 3\mathbf{v}
$$

Substituting:

$$
\begin{pmatrix}
1 & 2 \\
2 & 1
\end{pmatrix} \begin{pmatrix}
x \\
y
\end{pmatrix} = 3 \begin{pmatrix}
x \\
y
\end{pmatrix}
$$

Results in the system:

1. $$ x + 2y = 3x $$
2. $$ 2x + y = 3y $$

Choosing $$ x = 1 $$ leads to $$ y = 1 $$, yielding the eigenvector for $$ \lambda = 3 $$:

$$
\begin{pmatrix}
1 \\
1
\end{pmatrix}
$$

You can repeat similar calculations for $$ \lambda = -1 $$.
