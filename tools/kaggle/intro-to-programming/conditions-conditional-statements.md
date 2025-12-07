# (4) Conditions and Conditional Statements
https://www.kaggle.com/code/alexisbcook/conditions-and-conditional-statements

## 1. Conditions
- <strong>Conditions</strong> are statements that are either `True` or `False`.
- Possible write conditions in different ways, but most common to compare values.

```
print (2 > 3)
```
Output:
```
False
```
- Possible to compare values of variables.

```
var_one = 1
var_two = 2

print(var_one < 1)
print(var_two >= var_one)
```
Output:
```
False
True
```
<strong>Common symbols</strong>
- `==` equals
- `!=` does not equal
- `<` less than
- `<=` less than or equal to
- `>` greater than
- `>=` greater than or equal to

### Important Note: 
When you check two values are equal, make sure you use the == sign, and not the = sign.

## 2. Conditional Statements
<strong>Conditional statements</strong> use conditions to update how your function will run. 
- If one block is `True` that block will return, otherwise another block of the code will be executed.

### a. "if" statements
- An <strong>if statement</strong> runs a block of code when its condition is `True`.
- Example
```
if temp > 38:
   message = "Fever!"
```
- If the condition is <strong>False</strong>, the intended block is skipped.
- In the example function:
   - Default message `"Normal temp."`
   - if `temp > 38`, update to `"Fever"`
   - The `return` statement runs <strong>no matter what</strong>, because it's not inside the if-block.

#### Indentation Rules
Python uses intendation to define code blocks:
- First indentation level → inside a function.
- Second indentation level → inside an if / elif / else block

Correct indentation is crucial in Python

### b. "if ... else"
- <strong>else</strong> runs if the if-condition is <strong>False</strong>.
- Only one of the two code blocks runs:
  - if the condition is True → rund the `if` block.
  - otherwise → run the `else` block
- This version is clearer because both outcomes are explicitly defined.

### c. "if ... elif ... else"
Use `elif` (short for else if) to check <strong>multiple different conditions</strong>, in order:
1. Check first condition (`if`)
2. If False, check the next (`elif`)
3. If all previous conditions are False, run `else`

Example logic:
- if temp > 38 →`"Fever!"`
- Else if temp > 35 → `"Normal temperature."`
- Else → `"Low temperature."`  

Important:
- Only the <strong>first</strong> True condition runs.
- Once a match is found, Python <strong>skips the rest</strong>.

## 3. Example - Calculations
```
def get_taxes(earnings):
    if earnings < 12000:
        tax_owed = .25 * earnings
    else:
        tax_owed = .30 * earnings
    return tax_owed
```
The next code cell uses the function.
```
ana_taxes = get_taxes(9000)
bob_taxes = get_taxes(15000)

print(ana_taxes)
print(bob_taxes)
```
Output:
```
2250.0
4500.0
```
## 4. Example - Multiple "elif" statements
```
def get_dose(weight):
    # Dosage is 1.25 ml for anyone under 5.2 kg
    if weight < 5.2:
        dose = 1.25
    elif weight < 7.9:
        dose = 2.5
    elif weight < 10.4:
        dose = 3.75
    elif weight < 15.9:
        dose = 5
    elif weight < 21.2:
        dose = 7.5
    # Dosage is 10 ml for anyone 21.2 kg or over
    else:
        dose = 10
    return dose
```
- The order of the elif matters! With a different order the results will differ.

```
print(get_dose(12))
```
Output:
```
5
```