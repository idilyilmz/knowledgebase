# (2) Functions
https://www.kaggle.com/code/alexisbcook/functions

## 1. Intro to functions

A <strong>function</strong> in Python is made of two main parts: a <strong>header</strong> and a <strong>body</strong>.

### a. Header
- Starts with the keyword `def`
- Includes the <strong>function name</strong> (e.g., `add_three`)
- Has <strong>parantheses</strong> containing the function's <strong>argument(s)</strong> (e.g., `input_var`)
- Ends with a <strong>colon</strong> (`:`)
- Arguments are the input values the function will use. Functions can have zero, one, or many arguments.

### b. Body
- Contains the code that defines what the function does.
- <strong>Intented by exactly four spaces</strong> (or one Tab)
- Executes from top to bottom
- Uses the argument to perfirm opertaions (e.g., `output_var = input_var + 3`)
- Ends with a `return` <strong>statement</strong>, which sends a value back as the function's output.

<strong>Note</strong>:
Defining a function doesn't run it, you must call the function later for it to execite.

## 2. How to run (or "call") a function
To <strong>run / call</strong> a function in Python, you write the function's name followed by parantheses containing any required input values (args).

<strong>Example</strong>
```
new_number = add_three(10)
print(new_number)   # Output: 13
```

### What Happens When You Call `add_three(10)`
1. Python sends the value 10 into the function as `input_var`
2. Inside the function body:
    - It computes
      
      `output_var = input_var + 3`
      
      which becomes `output_var = 13`

3. The `return` statement sends <strong>13</strong> back as the result.
4. The line

`new_number = add_three(10)`

sets `new_number` equal to <strong>13</strong>

### Why do we write `add_three()` in Explanations
When referring to a function we write the function name like `add_three()` with empty parantheses. Just to show it's a function. Even if the method normally holds arguments.

## 3. Naming functions
When naming functions 
- use lowercase letters.
- seperate words with underscores (_), not spaces!
- naming them will be easier, the more code you write.

## 4. A more complex example
The Function `get_pay(num_hours)` calculates a weekly paycheck:
- Pretax pay = hours worked * $15
- After-tax pay = pretax pay * (1 - 0.12)
- The function returns the after-tax amount

```
def get_pay(num_hours):
    # Pre-tax pay, based on receiving $15/hour
    pay_pretax = num_hours * 15
    # After-tax pay, based on being in 12% tax bracket
    pay_aftertax = pay_pretax * (1 - .12)
    return pay_aftertax
```
Output: $528

```
# Calculate pay based on working 40 hours
pay_fulltime = get_pay(40)
print(pay_fulltime)
```
Output: 528.0

```
pay_parttime = get_pay(32)
print(pay_parttime)
```
Output 422.4

Example calls:
- `get_pay(40)` → 528.0
- `get_pay(32)` → 422.4

### Why using a method?
- avoids rewriting code
- reduces errors
- makes calculations quick and repeatable

## 5. Variable "scope"
Variables created inside a function (like `pre-pretax` or `pay_aftertax`) exist only within that function. Trying to access them outside causes a <strong>NameError</strong>.
- These are <strong>local</strong> variables.
- Variables created outside functions (like, `pay_parttime`) have <strong>global</strong> scope.

To use info from a function, it must be included in the return statement.

## 6. Functions with multiple arguments
You can add more inputs by seperating arguments with commas.

Example
```
def get_pay_with_more_inputs(num_hours, hourly_wage, tax_bracket):
    pay_pretax = num_hours * hourly_wage
    pay_aftertax = pay_pretax * (1 - tax_bracket)
    return pay_aftertax
```

Calling it:
- `get_pay_with_more_inputs(40, 24, 0.22)` → 748.8
- Setting wage = 15 & tax = 0.12 produces the same result as the simpler function.

### Use case:
This version is more flexible bacause the user can specify wage and tax rate. But it's more complex if those values never change.

## 7. Functions with no arguments
Functions can have
- no arguments
- no return value

Example
```
def print_hello():
    print("Hello, you!")
    print("Good morning!")
```

calling `print_hello()` simplyh prints messages.
