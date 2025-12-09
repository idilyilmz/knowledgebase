# (3) Booleans and Conditionals

## Booleans
a `bool` has two values. 
- `True`
- `False`

<strong>boolean operators</strong> are operators that answer yes/no questions.

### a. Comparison Operators

| Operation | Description                  |
|-----------|------------------------------|
| `a == b`  | a equal to b                 |
| `a < b`   | a less than b                |
| `a <= b`  | a less than or equal to b    |
| `a != b`  | a not equal to b             |
| `a > b`   | a greater than b             |
| `a >= b`  | a greater than or equal to b |

Example:
```
def can_run_for_president(age):
    """Can someone of the given age run for president in the US?"""
    # The US Constitution says you must be at least 35 years old
    return age >= 35

print("Can a 19-year-old run for president?", can_run_for_president(19))
print("Can a 45-year-old run for president?", can_run_for_president(45))
```

Output:
```
Can a 19-year-old run for president? False
Can a 45-year-old run for president? True`
```

Example
```
3.0 == 3
```

Output:
```
True
```
BUT 

Example
```
'3' == 3
```

Output:
```
False
```

Comparison operators combined with arithmetic operators

Example
```
def is_odd(n):
    return (n % 2) == 1

print("Is 100 odd?", is_odd(100))
print("Is -1 odd?", is_odd(-1))
```

Output:
```
Is 100 odd? False
Is -1 odd? True
```

#### Important
Remember to use == instead of = when making comparisons. If you write n == 2 you are asking about the value of n. When you write n = 2 you are changing the value of n.

### b. Combining Boolean Values
You combine booleans using the logical operators.
1. `and`
- True only if <strong>both</strong>
```
True and True   # True
True and False  # False
```
2. `or`
- True is at least one condition is true
```
True or False   # True
False or False  # False
```

3. `not`
- Flips a boolean value
```
not True   # False
not False  # True
```

#### Example with expressions
```
x = 5
(x > 2) and (x < 10)   # True
(x == 5) or (x == 7)   # True
not (x > 10)           # True
```
## Conditionals
<strong>Purpose of Conditionals</strong>
Conditionals let you run certain code only when a Boolean condition is true. They use the keywords: `if`, `elif` and `else`.

<strong>Basic structure</strong>
```
if condition:
    # code if condition is True
elif another_condition:
    # code if first is False but this one is True
else:
    # code if none of the above are True
```
- `elif` means "else if"
- Both `elif` and `else` are optional.
- You can have multiple `elif` blocks, but only one `else`

<strong>Example</strong>:
```
def inspect(x):
    if x == 0:
        print(x, "is zero")
    elif x > 0:
        print(x, "is positive")
    elif x < 0:
        print(x, "is negative")
    else:
        print(x, "is unlike anything I've ever seen...")
```

Calling:
```
inspect(0)   → 0 is zero
inspect(-15) → -15 is negative
```
<strong>Indentation Matters</strong>
Python uses colons (`:`) and indentation to mark code blocks.
- After `if`, `elif`, `else`, or a function definitions:
   - End the line with `:`
   - Indent the next line (typically 4 spaces)
- The block ends when the indentation returns to the previous level.

<strong>Example Showing Block Structure</strong>
```
def f(x):
    if x > 0:
        print("Only printed when x is positive; x =", x)
        print("Also only printed when x is positive; x =", x)
    print("Always printed, regardless of x's value; x =", x)
```
Calling
```
f(1)
f(0)
```
Output
```
Only printed when x is positive; x = 1
Also only printed when x is positive; x = 1
Always printed, regardless of x's value; x = 1
Always printed, regardless of x's value; x = 0
```

<strong>Key Ideas to Remember</strong>
- Conditionals run different code depending on Boolean conditions.
- `elif` chains multiple conditions.
- `else` catches anything not handled earlier.
- Indentation defines which lines belong to which block.

### a. Boolean conversion
`int()` turns things into ints
`float()` turns things into floats
`bool()` turns things into bools

Example
```
print(bool(1)) # all numbers are treated as true, except 0
print(bool(0))
print(bool("asf")) # all strings are treated as true, except the empty string ""
print(bool(""))
# Generally empty sequences (strings, lists, and other types we've yet to see like lists and tuples)
# are "falsey" and the rest are "truthy"
```

```
True
False
True
False
```