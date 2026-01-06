# (5) Loops and List Comprehensions

https://www.kaggle.com/code/colinmorris/loops-and-list-comprehensions

## 1. Loops

- a way to repeatedly execute some code.

```
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
    print(planet, end=' ') # print all on same line
```

Output:

```
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
    print(planet, end=' ') # print all on same line
```

Loops allow you to run code repeatedly.

A for-loop iterates over items in a collection such as a list, tuple, or even a string. <strong>Example: </strong> looping through a list of planets or printing uppercase letters in a sentence.

```
s = 'steganograpHy is the practicE of conceaLing a file, message, image, or video within another fiLe, message, image, Or video.'
msg = ''
# print all the uppercase letters in s, one at a time
for char in s:
    if char.isupper():
        print(char, end='')   
```

Output:

```
HELLO
```

`range()` produces a sequence of numbers and is useful when you want to loop a specific number of times.

```
for i in range(5):
    print("Doing important work. i =", i)
```

Output:

```
Doing important work. i = 0
Doing important work. i = 1
Doing important work. i = 2
Doing important work. i = 3
Doing important work. i = 4
```

### a. while loops

A while-loop keeps running as long as its condition is `True`. Example: increasing a counter until it reaches 10.

```
i = 0
while i < 10:
    print(i, end=' ')
    i += 1 # increase the value of i by 1
```

Output:

```
0 1 2 3 4 5 6 7 8 9 
```

The argument of the `while` loop is evaluated as a boolean statement, and the loop is executed until the statement evaluates to False.

## 2. List comprehensions

```
squares = [n**2 for n in range(10)]
squares
```

Output:

```
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

without a list comprehension

```
squares = []
for n in range(10):
    squares.append(n**2)
squares
```

Output:

```
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

List comprehensions provide a concise way to create lists. They combine looping, optional filtering with `if`, and optional transformations. For example, generating squares of numbers, filtering short planet names, or converting names to uppercase. They can replace longer for-loops, but readability should always be considered.

```
short_planets = [planet for planet in planets if len(planet) < 6]
short_planets
```

Output:

```
['Venus', 'Earth', 'Mars']
```

another example:

```
# str.upper() returns an all-caps version of a string
loud_short_planets = [planet.upper() + '!' for planet in planets if len(planet) < 6]
loud_short_planets
```

Output:

```
['VENUS!', 'EARTH!', 'MARS!']
```

over multiple lines

```
[
    planet.upper() + '!' 
    for planet in planets 
    if len(planet) < 6
]
```

Output:

```
['VENUS!', 'EARTH!', 'MARS!']
```

When counting items that meet a condition (like negative numbers), list comprehensions—or even using boolean arithmetic—can create very short solutions, but readability is still important, following “The Zen of Python.”

```
def count_negatives(nums):
    # Reminder: in the "booleans and conditionals" exercises, we learned about a quirk of 
    # Python where it calculates something like True + True + False + True to be equal to 3.
    return sum([num < 0 for num in nums])
```

Output:

```
Readability counts.
Explicit is better than implicit.
```