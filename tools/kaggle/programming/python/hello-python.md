# (1) Hello, Python
https://www.kaggle.com/code/colinmorris/hello-python

## 1. Hello, Python
### Variable assignment:
```
spam_amount = 0
```
- `=` is the <strong>assignment operator</strong>
- Python does not require
  - declaring variables beforehand
  - specifying variable types
- variables can later be reassigned to different types (strings, numbers, etc.).

### Function calls:
```
print(spam_amount)
```
- `print()` is a function call
- functions use:
   - function name
   - parantheses
   - arguments inside parantheses


### Comment:
```
# This is a comment
```
- begin with `#`
- used to explain code, ignoring by Python

### Reassignment
```
spam_amount = spam_amount + 6
```
- Python evaluates the right side first
- Reassigns the variable to the new value
- Example: `0 + 4 = 4`

### Conditionals (if statement)
```
if spam_amount > 0:
    print("But I don't want ANY spam!")
```
- `if` checks a condition (True / False)
- A colon `:` starts a new <strong>code block</strong>.
- Code inside the block must be indented (4 spaces)
- Code outside the indent runs whether or not the condition is met

<strong>Important</strong>
Python uses <strong>indentation</strong> instead of `{}` braces like other languages.

### String:
- Text enclosed in quotes
- Can use single or double quotes
- Use double quotes if the string contains `'` inside.

Example
```
"But I don't want ANY spam!"
```

### Operator Overloading
```
viking_song = "Spam " * spam_amount
```
- `*` normally does multiplication
- With strings, `"Spam " * 4` repeats string 4 times
- Many Python operators behave differently depending on data types.
```
Spam Spam Spam Spam 
```

### a. Numbers and arithmetic in Python

#### Integer
Any whole number can be positive( 1, 2, 3), negative (-1, -2, -3) or zero (0).

#### Float
A number with a decimal place.

An `//` operator gives a result that is rounded to the next integer

```
print(5 // 2)
print(6 // 2)
```
Output:
```
2
3
```

| Operator | Name            | Description                                      |
|----------|-----------------|--------------------------------------------------|
| `a + b`  | Addition        | Sum of a and b                                   |
| `a - b`  | Subtraction     | Difference of a and b                            |
| `a * b`  | Multiplication  | Product of a and b                               |
| `a / b`  | True division   | Quotient of a and b                              |
| `a // b` | Floor division  | Quotient of a and b, removing fractional parts   |
| `a % b`  | Modulus         | Integer remainder after division of a by b       |
| `a ** b` | Exponentiation  | a raised to the power of b                       |
| `-a`     | Negation        | The negative of a                                |

#### Order of Operations
PEMDA S
1. Parantheses
2. Exponents
3. Multiplication / Division
4. Addition / Substraction

#### Builtin functions for working with numbers
`min` and `max`
```
print(min(1, 2, 3))
print(max(1, 2, 3))
```
Output:
```
1
3
```

`abs` returns the absolute value
```
print(abs(32))
print(abs(-32))
```
Output:
```
32
32
```

`int` and `float`
```
print(float(10))
print(int(3.33))
# They can even be called on strings!
print(int('807') + 1)
```
Output:
```
10.0
3
808
```