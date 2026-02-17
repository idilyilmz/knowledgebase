# Module 3: Calculus

## 4. The Quotient Rule - Introduction

In this lesson you will learn about:
- The quotient rule.

For this lesson you should be familiar with:
- The concept differentiation.
- How to differentiate elementary functions.

### Calculating the Derivative of a Quotient of Two Functions

#### Example: Derivative of $$ \frac{\ln(x)}{x^2 + 3} $$
- **Functions**: The expression $$ \frac{\ln(x)}{x^2 + 3} $$ is a quotient of two functions:
  - $$ f(x) = \ln(x) $$
  - $$ g(x) = x^2 + 3 $$

#### Quotient Rule for Derivatives
- The derivative of a quotient of two functions is given by:
  $$
  \frac{d}{dx}\left( \frac{f(x)}{g(x)} \right) = \frac{f'(x) \cdot g(x) - f(x) \cdot g'(x)}{(g(x))^2}
  $$

#### Standard Derivatives
- **Calculating derivatives**:
  - $$ f'(x) = \frac{d}{dx}(\ln(x)) = \frac{1}{x} $$
  - $$ g'(x) = \frac{d}{dx}(x^2 + 3) = 2x $$

#### Solution
- Applying the quotient rule:
  $$
  \frac{d}{dx}\left( \frac{\ln(x)}{x^2 + 3} \right) = \frac{\frac{1}{x} (x^2 + 3) - \ln(x) \cdot 2x}{(x^2 + 3)^2}
  $$

Thus, the derivative is:
$$
\frac{x^2 + 3 - 2x \ln(x)}{(x^2 + 3)^2}
$$