# Module 3: Calculus

## 5. The Chain Rule - Introduction

In this lesson you will learn about:
- The chain rule.

For this lesson you should be familiar with:
- The concept differentiation.
- How to differentiate elementary functions.

### Calculating the Derivative of a Composite Function

#### Example: Derivative of $$ (x^2 + 3)^3 $$

- **Composite Function**: The expression $$ (x^2 + 3)^3 $$ can be represented as $$ g(f(x)) $$, where:
  - $$ f(x) = x^2 + 3 $$
  - $$ g(x) = x^3 $$

#### Chain Rule for Derivatives

- The derivative of a composite function is given by:
  $$
  \frac{d}{dx}g(f(x)) = g'(f(x)) \cdot f'(x)
  $$

#### Standard Derivatives

- **Calculating derivatives**:
  - $$ f'(x) = \frac{d}{dx}(x^2 + 3) = 2x $$
  - $$ g'(x) = \frac{d}{dx}(x^3) = 3x^2 $$

#### Solution

- Applying the chain rule, we get:
  $$
  \frac{d}{dx}(x^2 + 3)^3 = 3(x^2 + 3)^2 \cdot 2x = 6x(x^2 + 3)^2
  $$

Thus, the derivative of $$ (x^2 + 3)^3 $$ is **$$ 6x(x^2 + 3)^2 $$**.