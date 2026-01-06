# (2) Functions and Getting Help
https://www.kaggle.com/code/colinmorris/functions-and-getting-help

## Getting Help

```
help(round)
```

### 1. `help()` is one of the most important Python functions

It shows you <strong>how a function works</strong> and <strong>what arguments it accepts</strong>.

Using `help()` effectively lets you figure out almost any built-in function.

### 2. What `help()` displays

It typically shows:
1. <strong>The function signature</strong>,
    `round(number, ndigits=None)`
2. <strong>A description</strong> of what the function does.

### 3. Common mistake: don’t call the function inside `help()`

- Correct: `help(round)`
- Incorrect: `help(round(-2.01))`

When you do the incorrect one, Python:
- First evaluates `round(-2.01)` → produces an integer
- Then gives you help for the result type, not the function you intended → `help(int)`.

### 4. Example: `help(print)`

You can learn:
- `print()` accepts optional keyword arguments:
   - `sep` → string placed between printed items
   - `end` → string appended at the end
   - `file` → where to send the output
   - `flush` → whether to flush output immediately

#### Core takeaway


Always pass the function itself (without parentheses) to `help()` to see how it works.
Example:
```
help(abs)
help(print)
help(len)
```

This gives you the official documentation for that function.

### a. Defining functions

Below is an example of a built-in function
```
def least_difference (a, b, c):
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
```

When Python encounters a `return` statement, it exists the function immediately, and passes the value on the right hand side to the calling context.

`least_difference()` in practice

```
print(
    least_difference(1, 10, 100),
    least_difference(1, 10, 10),
    least_difference(5, 6, 7), # Python allows trailing commas in argument lists. How nice is that?
)
```

Output:

```
9 0 1
```

`help()` in practice

```
help(least_difference)
```

Output:

```
Help on function least_difference in module __main__:

least_difference(a, b, c)
```

#### a_a. Docstrings

```
def least_difference(a, b, c):
    """Return the smallest difference between any two numbers
    among a, b and c.
    
    >>> least_difference(1, 5, -5)
    4
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
```
The `docstring` is a string with three quotes. These can be span over multiple lines. The docstring comes immediately after the header of a function. 

Docstrings include sometimes an example function call. These are maerked with `>>>`, like in Python's interactive shell. These examples aren't executed by Python. They're there for the reader. The doctstrings can be very helpful.

### a_b. Functions that don't return

Without a `return` statement, the result of calling the functions is the special value `None`. 
```
def least_difference(a, b, c):
    """Return the smallest difference between any two numbers
    among a, b and c.
    """
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    min(diff1, diff2, diff3)
    
print(
    least_difference(1, 10, 100),
    least_difference(1, 10, 10),
    least_difference(5, 6, 7),
)
```

Output:
```
None None None 
```

### a_c. Default arguments

`sep`

```
print(1, 2, 3, sep=' < ')
```
Output:
```
1 < 2 < 3
```

without `sep`
```
print(1, 2, 3)
```
Output:
```
1 2 3
```

Add optional arguments with default values to functions.
```
def greet(who="Colin"):
    print("Hello,", who)
    
greet()
greet(who="Kaggle")
# (In this case, we don't need to specify the name of the argument, because it's unambiguous.)
greet("world")
```
Output:
```
Hello, Colin
Hello, Kaggle
Hello, world
```

### d. Functions Applied to Functions

#### Functions can be passed as argumnets

- In Python, functions are "first-class objects"
- This means you can:
   - Pass functions into other functions
   - Return functions
   - Store function variables

Example
```
def mult_by_five(x):
    return 5 * x

def call(fn, arg):
    """Call fn on arg"""
    return fn(arg)

def squared_call(fn, arg):
    """Call fn on fn(arg)"""
    return fn(fn(arg))
```

Output:
```
call(mult_by_five, 1)        → 5
squared_call(mult_by_five, 1) → mult_by_five(mult_by_five(1)) = 25
```

#### Higher-order functions

A <strong>higher-order function</strong> is any function that:
- Takes another function as input, or 
- Returns a function

Python includes many built-in higher-order functions (`map`, `sorted`, `max` with a key)

#### Using `max` with the `key` argument

- `max()` normally returns the largest value
- but with 'key=my_method', it instead returns the value that maximizes `key(x)` (the argmax)

Example #1
```
def mod_5(x):
    return x % 5
```
Example #2
```
max(100, 51, 14)              → 100
max(100, 51, 14, key=mod_5)   → 14   (because 14 % 5 = 4, the largest remainder)
```

#### Key idea

Higher-order functions let you customize behavior by supplying your own logic through a function.

They enable more abstract, flexible programming patterns.