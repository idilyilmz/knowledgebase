# (4) Lists
https://www.kaggle.com/code/colinmorris/lists

List
```
primes = [2, 3, 5, 7]
```
Other things in lists
```
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
```

List of lists
```
hands = [
    ['J', 'Q', 'K'],
    ['2', '2', '2'],
    ['6', 'A', 'K'], # (Comma after the last element is optional)
]
# (I could also have written this on one line, but it can get hard to read)
hands = [['J', 'Q', 'K'], ['2', '2', '2'], ['6', 'A', 'K']]
```

list with different kinds of variables
```
my_favourite_things = [32, 'raindrops on roses', help]
# (Yes, Python's help function is *definitely* one of my favourite things)
```
## Indexing
accessing individual elements with square brackets.

```
planets[0]
```

Output:
```
'Mercury'
```

but `planets[2]` would output `'Earth'`

Elements at the end of the list can be accessed with negative numbers, starting from -1.
```
planets[-1]
```

Output:
```
'Neptune'
```
## Slicing
```
planets[0:3]
```
Output:
```
['Mercury', 'Venus', 'Earth']
```

Example
```
planets[:3]
```
Output
```
['Mercury', 'Venus', 'Earth']
```

Example
```
planets[3:]

```
Output
```
['Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
```
Negative indices when slicing

Example
```
# All the planets except the first and last
planets[1:-1]
```
Output
```
['Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus']
```

Example
```
# The last 3 planets
planets[-3:]
```
Output
```
['Saturn', 'Uranus', 'Neptune']
```

## Changing lists
Lists can be changable in place. That means that lists are "mutable".

So in the planets example if you do
```
planets[3] = 'Malacandra'
planets
```
Output:
```
['Mercury',
 'Venus',
 'Earth',
 'Malacandra',
 'Jupiter',
 'Saturn',
 'Uranus',
 'Neptune']
```
## List functions
`len` gives the length of a list
```
# How many planets are there?
len(planets)
```
Output:
```
8
```

`sorted` returns a sorted version of a list

`sum` returns a sum of a list

`max` gives the highest value

## Interlude: Objects
- In python, everything is an object.
- Objects carry data and functionality with them. You access these using dot syntax (`object.something`)

### Attributes
- Are stored inside an object

Example
```
x = 12
x.imag   # imaginary part → 0
```

### Methods
- Are functions attached to an object.
- Accessed using dot syntax and called with parantgeses.

Example
```
x.bit_length()  # returns number of bits needed to represent x
```

### use `help()` on methods
example
```
help(x.bit_length)
```

### Main idea
- Objects have attributes (data) and methods (functions).
- Numbers, booleans, and functions don't have many useful methods, but lists (coming next) have many you’ll use regularly.

## List methods
`list.append` updates a list by adding an item to the end.
```
# Pluto is a planet darn it!
planets.append('Pluto')
```
Output adds pluto at the end of the list.

`list.pop` removes and returns the last element of a list.

Example
```
planets.pop()
```

Output:
```
'Pluto'
```

And
```
planets
```
Output:
```
['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
```

### Searching lists
`list.index` gets the index.
```
planets.index('Earth')
```
Output:
```
2
```

When you try to search for a value that's not existing. To avoid getting an error you can use the `in` operator.
```
# Is Earth a planet?
"Earth" in planets
```
Output
```
True
```

Or
```
# Is Calbefraques a planet?
"Calbefraques" in planets
```

Output:
```
False
```
## Tuples
- use parantheses `(1, 2, 3)` instead of square brackets `[ 1, 2, 3]`
- can't be modified

`as_integer_ratio()` method of float objects returns a numerator and a denominator in the form of a tuple.

