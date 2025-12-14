# (7) Working with External Libraries

## 1. Imports
<strong>a. Importing modules</strong>
- Python can load extra code using import, including the standard library and external libraries.
- import math loads the math module, which contains functions and constants (e.g., math.pi, math.log()).
- dir(module) shows all names available inside a module.
- help(function_or_module) gives documentation.

<strong>b. Import variants</strong>
- import math as mt creates a shorter alias.
- from math import * imports everything into the current namespace
    → convenient but risky because names can conflict.
- Better practice: import only what you need:
   `from math import log, pi`

<strong>c. Submodules</strong>
- Modules can contain other modules, e.g., numpy.random.
- Access them with multiple dots: numpy.random.randint().

### a. Oh the places you'll go, oh the objects you'll see
- Libraries introduce many custom object types (e.g., NumPy arrays, pandas DataFrames, matplotlib Figures).
- You must understand how to interact with these types because they have unique behaviors.

### b. Three tools for understanding strange objects
<strong>a. `type()` — What is this thing?</strong>
- Tells you the object’s type, e.g., `numpy.ndarray`.

<strong>b. `dir()` — What can I do with it?</strong>
- Lists all attributes and methods the object supports.

<strong>c. `help()` — Tell me more</strong>
- Gives detailed documentation for methods and classes.

### c. Operator overloading
- Python allows types to redefine how operators behave.
- Example: Lists can’t do `[1,2,3] + 10`, but NumPy arrays can: `array + 10` adds 10 to each element.
- Operators like `+`, `<=`, indexing, and boolean logic may behave very differently depending on the object type.
- Libraries like TensorFlow overload operators to build computation graphs (e.g., `a + b` returns a Tensor, not a number).

### d. Special double-underscore methods
- Operators internally call special “dunder” methods:
   - `__add__` for `+`
   - `__contains__` for `in`
   - `__getitem__` for indexing
- Listing a type’s dir shows these methods.
- Knowing these can help you understand unusual behaviors in libraries.