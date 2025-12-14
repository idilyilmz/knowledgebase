# (6) Strings and Dictionaries

https://www.kaggle.com/code/colinmorris/strings-and-dictionaries

## Strings

### a. String syntax
- Strings can use single (`' '`) or double (`" "`) quotes — they work the same.
- To include quotes inside strings, use the opposite quote type or escape with `\`.
- `\n` creates a newline; `\\` creates a backslash.
- Triple quotes (`""" """`) allow multi-line strings.
- `print()` adds a newline by default unless you change end=.

| What you type... | What you get | example                  | print(example)       |
|------------------|--------------|--------------------------|----------------------|
| \'               | '            | 'What\'s up?'            | What's up?           |
| \"               | "            | "That's \"cool\""        | That's "cool"        |
| \\               | \            | "Look, a mountain: /\\"  | Look, a mountain: /\ |
| \n               |              | "1\n2 3"                 | 1 *enter* 2 3        |

### b. Strings are sequences
- You can index and slice strings like lists.
- Strings are immutable — they cannot be modified in place.
- You can loop over characters.
- `len()` gives the string’s length.

### c. String methods
- Useful methods include:
   - `.upper()`, `.lower()` for case conversion
   - `.index()` to find a substring
   - `.startswith()` / `.endswith()`
- `split()` converts a string to a list of words (or other separators).
- `join()` combines a list of strings into one string with a chosen separator.
- String building:
   - `+` concatenates strings.
   - `str.format()` inserts values using `{}` placeholders and supports formatting options (decimals, percentages, commas, indexing, etc.).

## Dictionaries
- Dictionaries map keys to values using `{}`.
- Access values with `dict[key]`.
- Add or update entries using the same syntax.
- Dictionary comprehensions allow building dictionaries from loops.
- `in` checks whether a key exists.
- Looping over a dictionary iterates over keys.
- `dict.keys()`, `dict.values()`, and `dict.items()` give access to keys, values, or both.
- You can iterate over key–value pairs directly with `.items()`.