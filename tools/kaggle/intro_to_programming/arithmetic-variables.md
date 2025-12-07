# (1) Arithmetic and variables

https://www.kaggle.com/code/alexisbcook/arithmetic-and-variables

## 1. Printing
<strong>code cell</strong>

```
print("Hello, world!")
```

<strong>Output</strong> of the code:

`Hello, world!`

## 2. Arithmetic
Arithmetic operations:
- addition (+)
- substraction (-)
- multiplication (*)
- division (/)
- exponent (**)

Addition
```
print( 1 + 2 )
```
<strong>Output</strong> of the code:
3

Substraction
```
print( 9 - 2 )
```
<strong>Output</strong> of the code:
7

Multiplication
```
print( 2 * 4 )
```
<strong>Output</strong> of the code:
8

Division
```
print( 6 / 3 )
```
<strong>Output</strong> of the code:
2

Exponent
```
print( 3 ** 2 )
```
<strong>Output</strong> of the code:
9

Use <strong>paranthesis</strong> to control the order op operations
```
print(((1 + 3) * (9 - 2) / 2) ** 2)
```
<strong>Output</strong> of the code:
196.0

## 3. Comments

Comments help understanding the code. Or what the method or code is doing.

```
# Multiply 3 by 2
print(3 * 2)
``` 

## 4. Variables

### 4.1 Creating variables

```
# Create a variable called test_var and give it a value of 4+5
test_var = 4 + 5

# Print the value of test_var
print(test_var)
```

Select a name you want to use (short and descriptive)

Need to have:
- can't have spaces
- only letters, numbers, underscores
- start with letter or underscore

use = to assign

peek at what the value of the var is by using
```
print()
```

### 4.2 Manipulating variables
Possible to override existing variable

```
# Set the value of a new variable to 3
my_var = 3

# Print the value assigned to my_var
print(my_var)

# Change the value of the variable to 100
my_var = 100

# Print the new value assigned to my_var
print(my_var)
```

as long as the code is in the same code cell, you can print the variable name. Or reassign it like
```
my_var = my_var + 4
print(my_var)
```
<strong>Output</strong> of the code:
104

### 4.3 Using multiple variables
Its possible to assign numbers to variables and do math using the variable names instead of the numbers. For example like doing math with time.
```
# Create variables
num_years = 4
days_per_year = 365 
hours_per_day = 24
mins_per_hour = 60
secs_per_min = 60

# Calculate number of seconds in four years
total_secs = secs_per_min * mins_per_hour * hours_per_day * days_per_year * num_years
print(total_secs)
```

### 4.4 Debugging
```
print(hours_per_day)
```