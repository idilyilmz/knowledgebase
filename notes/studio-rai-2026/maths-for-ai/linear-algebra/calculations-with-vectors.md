# Module 2: Linear Algebra

## 4. Calculations with Vectors

In this worked example you will learn about:
- Addition of vectors.
- Scalar multiplication of vectors.

For this worked example you are assumed to be familiar with:
- What vectors are.

### Vector Calculations

#### Addition

Vectors are added **componentwise**. For vectors 

$$\mathbf{a} = (a_1, a_2, \ldots, a_n)$$ 

and 

$$\mathbf{b} = (b_1, b_2, \ldots, b_n)$$

$$
\mathbf{a} + \mathbf{b} = (a_1 + b_1, a_2 + b_2, \ldots, a_n + b_n)
$$

##### Example

For 

$$\mathbf{a} = (1, 2, 3)$$ 

and 

$$\mathbf{b} = (4, 5, 6)$$

$$
\mathbf{a} + \mathbf{b} = (1 + 4, 2 + 5, 3 + 6) = (5, 7, 9)
$$

**Note**: Vectors of different sizes cannot be added:

$$
\mathbf{a} + \mathbf{b} \quad \text{is not defined if} \quad n \neq m
$$

##### Example

For 

$$\mathbf{a} = (1, 2, 3)$$

and 

$$\mathbf{b} = (4, 5, 6, 7)$$

$$
\mathbf{a} + \mathbf{b} \quad \text{is not defined}
$$

#### Scalar Multiplication

Vectors can be multiplied by a **scalar** (a real number) componentwise. For a scalar 

$$\lambda$$

and vector 

$$\mathbf{a} = (a_1, a_2, \ldots, a_n)$$

$$
\lambda \cdot \mathbf{a} = (\lambda \cdot a_1, \lambda \cdot a_2, \ldots, \lambda \cdot a_n)
$$

##### Example

For 

$$\lambda = 3$$

and 

$$\mathbf{a} = (1, 2, 3)$$

$$
3 \cdot \mathbf{a} = (3 \cdot 1, 3 \cdot 2, 3 \cdot 3) = (3, 6, 9)
$$
