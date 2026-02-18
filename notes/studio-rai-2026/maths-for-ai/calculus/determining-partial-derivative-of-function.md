# Module 3: Calculus

## 12. Determining the Partial Derivative of a Function

In this lesson you will learn about:
- How to find the partial derivative of a function.

For this lesson you should be familiar with:
- The concept differentiation.
- How to differentiate elementary functions.

### Finding the Partial Derivative of a Function

#### Example: Partial Derivative of $$ x^3 + x^2 \ln(y) + y^2 $$

#### Understanding Partial Differentiation

- **Partial differentiation** involves finding the derivative with respect to one variable while treating all other variables as constants.

#### Problem Setup

- We want to find:
  $$
  \frac{\partial}{\partial x}(x^3 + x^2 \ln(y) + y^2)
  $$

#### Simplifying the Expression

- Apply the addition rule:
  $$
  \frac{\partial}{\partial x}(x^3) + \frac{\partial}{\partial x}(x^2 \ln(y)) + \frac{\partial}{\partial x}(y^2)
  $$

#### Solving the Separate Derivatives

1. **First Term**:
   $$
   \frac{\partial}{\partial x}(x^3) = 3x^2
   $$
2. **Second Term**:
   $$
   \frac{\partial}{\partial x}(x^2 \ln(y)) = 2x \cdot \ln(y) \quad (\text{since } \ln(y) \text{ is constant})
   $$
3. **Third Term**:
   $$
   \frac{\partial}{\partial x}(y^2) = 0 \quad (\text{since } y^2 \text{ is constant})
   $$

#### Final Solution

- Combine the parts:
  $$
  \frac{\partial}{\partial x}(x^3 + x^2 \ln(y) + y^2) = 3x^2 + 2x \ln(y) + 0
  $$
  
The final result is:
$$
\frac{\partial}{\partial x}(x^3 + x^2 \ln(y) + y^2) = 3x^2 + 2x \ln(y)
$$