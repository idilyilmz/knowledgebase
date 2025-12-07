# (5) Intro to lists
https://www.kaggle.com/code/alexisbcook/intro-to-lists
## 1. Motivation
- A long string of items (like flower species) is hard to work with
- A <strong>list</strong> lets you:
  - access items by position
  - check how many items there are
  - easily add or remove items
- Lists are created with <strong>square brackets</strong> and <strong>comma-seperated items</strong>.

```
flowers = "pink primrose,hard-leaved pocket orchid,canterbury bells,sweet pea,english marigold,tiger lily,moon orchid,bird of paradise,monkshood,globe thistle"

print(type(flowers))
print(flowers)
```

Output:
```
<class 'str'>
pink primrose,hard-leaved pocket orchid,canterbury bells,sweet pea,english marigold,tiger lily,moon orchid,bird of paradise,monkshood,globe thistle
```
## 2. Lists
```
flowers_list = ["pink primrose", "hard-leaved pocket orchid", "canterbury bells", "sweet pea", "english marigold", "tiger lily", "moon orchid", "bird of paradise", "monkshood", "globe thistle"]

print(type(flowers_list))
print(flowers_list)
```
Output:
```
<class 'list'>
['pink primrose', 'hard-leaved pocket orchid', 'canterbury bells', 'sweet pea', 'english marigold', 'tiger lily', 'moon orchid', 'bird of paradise', 'monkshood', 'globe thistle']
```
### a. Length
- count number of entries with `len()`. Short for "length"

```
# The list has ten entries
print(len(flowers_list))
```
Output:
```
10
```

### b. Indexing
- Python uses <strong>zero-based indexing</strong>:
    - Index 0 → first item
    - Index 1 → second item
    - Last item → index `len(list) - 1`

Example:
```
flowers_list[0] # first item
flowers_list[9] # last item
```

### c. Slicing
Getting subsets of a List
- First x items → `list[:x]`
- Last y items → `list[-y:]`

Examples
```
flowers_list[:3]     # first 3 items
flowers_list[-2:]    # last 2 items
```
→ Returns a <strong>new list</strong>.

### d. Removing items
Remove an item from a list with `.remove()`, and put the item you would like to remove in parantheses.

```
flowers_list.remove("globe thistle")
print(flowers_list)
```
Output:
```
['pink primrose', 'hard-leaved pocket orchid', 'canterbury bells', 'sweet pea', 'english marigold', 'tiger lily', 'moon orchid', 'bird of paradise', 'monkshood']
```

### e. Adding Items
Adds an item to a list with `.append()`, and put the item you would like to add in parantheses. 

```
flowers_list.append("snapdragon")
print(flowers_list)
```
Output:
```
['pink primrose', 'hard-leaved pocket orchid', 'canterbury bells', 'sweet pea', 'english marigold', 'tiger lily', 'moon orchid', 'bird of paradise', 'monkshood', 'snapdragon']
```

### f. Lists are not just for strings

#### Lists can hold any data type
Example list of integers:
```
hardcover_sales = [139, 128, 172, 139, 191, 168, 170]
```
You can still 
- get length → `len(hardcover_sales)`
- index → `hardcover_sales[2]`
- get min/max → `min()`, `max()`
- sum all items → `sum()`

Example:
```
sum (hardcover_sales)    #total = 1107
```

#### Using slices in Calculations

You can compute on part of the list
```
sum(hardcover_sales[:5]) / 5
```