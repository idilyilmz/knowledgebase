# (3) Data Types
https://www.kaggle.com/code/alexisbcook/data-types

## 1. Integers
- Numbers without any fractional part 
- Can be positive (1, 48, 964)
- Can be negative (-4, -92, -729)
- Zero (0)

```
x = 14
print(x)
print(type(x))
```
Output:
```
14
<class 'int'>
```
<class 'int'> refers to integer data type

## 2. Floats
- Numbers with fractional parts.
- Can have many numbers after decimal.
- Any number with a deciman point will be recognized as a float (1.0, 1.00, etc.).
-  `.round()` let's you round a number to a specified number of decimal places.

### Example 1
```
nearly_pi = 3.141592653589793238462643383279502884197169399375105820974944
print(nearly_pi)
print(type(nearly_pi))
```
Output:
```
3.141592653589793
<class 'float'>
```

### Example 2
```
almost_pi = 22/7
print(almost_pi)
print(type(almost_pi))
```
Output:
```
3.142857142857143
<class 'float'>
```

### Example 3
```
# Round to 5 decimal places
rounded_pi = round(almost_pi, 5)
print(rounded_pi)
print(type(rounded_pi))
```
Output:
```
3.14286
<class 'float'>
```
### Example 4
```
y_float = 1.
print(y_float)
print(type(y_float))
```
Output:
```
1.0
<class 'float'>
```

## 3. Booleans
- True
- False

### Example 1
```
z_one = True
print(z_one)
print(type(z_one))
```
Output:
```
z_one = True
print(z_one)
print(type(z_one))
```

### Example 2
```
z_two = False
print(z_two)
print(type(z_two))
```
Output:
```
False
<class 'bool'>
```

### Example 3
```
z_three = (1 < 2)
print(z_three)
print(type(z_three))
```
Output:
```
True
<class 'bool'>
```

### Example 4
```
z_four = (5 < 3)
print(z_four)
print(type(z_four))
```
Output:
```
False
<class 'bool'>
```

### Example 5
```
z_five = not z_four
print(z_five)
print(type(z_five))
```
Output:
```
True
<class 'bool'>
```

## 4. Strings
- a collection of characters, contained in quotes ("")
  - alfphabet letters
  - punctualtion
  - numerical digits
  - symbols
- `len()` shows you the length of the string
- sometimes a string is convertable to a `float()` this will only work with digits!
- possible to add multiple strings
- can't do substraction or division with two strings
- can't multiply two strings
- CAN multiple a string with integer(s) 
- can't multiply with a float!

### Example 1
```
w = "Hello, Python!"
print(w)
print(type(w))
```
Output:
```
Hello, Python!
<class 'str'>
```
### Example 2
```
print(len(w))

```
Output:
```
14
```
### Example 3
```
shortest_string = ""
print(type(shortest_string))
print(len(shortest_string))
```
Output:
```
<class 'str'>
0
```
### Example 4
```
my_number = "1.12321"
print(my_number)
print(type(my_number))
```
Output:
```
1.12321
<class 'str'>
```
### Example 5
```
also_my_number = float(my_number)
print(also_my_number)
print(type(also_my_number))
```
Output:
```
1.12321
<class 'float'>
```
### Example 6
```
new_string = "abc" + "def"
print(new_string)
print(type(new_string))
```
Output:
```
abcdef
<class 'str'>
```
### Example 7
```
newest_string = "abc" * 3
print(newest_string)
print(type(newest_string))
```
Output:
```
abcabcabc
<class 'str'>
```
### Example 8
```
will_not_work = "abc" * 3.
```
Error output:
```
----------------------------------------------------------
TypeError                                 Traceback (most recent call last)
/tmp/ipykernel_19/2386798361.py in <module>
----> 1 will_not_work = "abc" * 3.

TypeError: can't multiply sequence by non-int of type 'float'
```
