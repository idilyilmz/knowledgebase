# Module 2: Linear Algebra

## 5. Multiplying Vectors by Matrices

In this worked example you will learn about:
- How to multiply vectors by matrices.

For this worked example you are assumed to be familiar with:
- What vectors are.
- What matrices are.

### General Rule

A vector in 

$$ \mathbb{R}^n $$

(with 

$$ n $$

elements) can be multiplied by a 

$$ m \times n $$

matrix. The multiplication is defined as:

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
\end{pmatrix}
$$

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

A vector in 
$$ \mathbb{R}^n $$
cannot be multiplied by a 
$$ m \times k $$
matrix if
$$ k \neq n $$

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
