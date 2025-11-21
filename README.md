# Python Interview Prep

## Basics

### Built-in Functions

```python
# Type Conversion
int('42')            # String to int
str(42)              # Int to string
list('abc')          # String to list
''.join(['a','b'])   # List to string
set([1,2,2])         # List to set

# Math
abs(-5)              # Absolute value
round(3.14159, 2)    # Round to decimals
```

### Strings
```python
s = "hello world"

# Essential Methods
s.split()            # Split on whitespace to a list
s.strip()            # Remove leading/trailing whitespace
s.lower()            # Convert to lowercase
s.upper()            # Convert to uppercase
s.find('sub')        # Index of substring (-1 if not found)
s.count('sub')       # Count occurrences

# Notes
s = s + "!"          # strings immutable, concat is O(n)
```

### Lists

```python
nums = [1,2,3]

# Common Operations
nums.index(1)      # Find index
nums.append(1)     # Add to end
nums.insert(0,10)  # Add 10 from left (at index 0 which is start)
nums.remove(3)     # Remove value
nums.pop()         # Remove & return last element
nums.sort()        # In-place sort (TimSort: O(n log n))
nums.reverse()     # In-place reverse
nums.copy()        # Return shallow copy

# List Slicing
nums[start:stop:step]  # Generic slice syntax
nums[-1]    # Last item
nums[::-1]  # Reverse list
nums[1:]    # Everything after index 1
nums[:3]    # First three elements

# Notes
```

### Dictionary

```python
d = {'a':1, 'b':2}

# Essential Operations
d.get('key', 0)       # safe access with default
d['key'] = 3          # add/update key
d.pop('key', None)    # remove key safely
d.keys()              # view all keys
d.values()            # view all values
d.items()             # view all key-value pairs

# Notes

```

### Sets

```python
# Sets are unordered, unique, O(1) average lookup
s = {1, 2, 3}        # empty set: s = set()

# Common Operations
s.add(4)             # Add element
s.remove(4)          # Remove (raises error if missing)
s.discard(4)         # Remove (no error if missing)
s.pop()              # Remove and return arbitrary element

# Notes

```

### Tuples
```python
# Tuples are immutable lists
t = (1, 2, 3, 1)

# Essential Operations
t.count(1)      # Count occurrences of value
t.index(2)      # Find first index of value

# Useful Patterns
x, y = (1, 2)   # Tuple unpacking
coords = [(1,2), (3,4)]  # Tuple in collections

# Notes
```

## Data Structures and Algorithms

| Data Structure              | Operation              | Time Complexity |
|-----------------------------|------------------------|------------------|
| **Array**                   | Access                 | O(1)            |
|                             | Search                 | O(n)            |
|                             | Insert                 | O(n)            |
|                             | Delete                 | O(n)            |
| **HashMap / HashSet**       | Search                 | O(1)            |
|                             | Insert                 | O(1)            |
|                             | Delete                 | O(1)            |
| **Linked List**             | Search                 | O(n)            |
|                             | Insert (given node)    | O(1)            |
|                             | Delete (given node)    | O(1)            |
| **Stack / Queue**           | Push / Enqueue         | O(1)            |
|                             | Pop / Dequeue          | O(1)            |
| **Binary Tree (Balanced)**  | Search                 | O(log n)        |
|                             | Insert                 | O(log n)        |
|                             | Delete                 | O(log n)        |


#### Common Patterns
-   Array / String / Linked List traversal
-   Hashing basics (set)
-   Two Pointers
-   Sliding Window
-   Frequency map
-   Prefix sums
-   Binary search
-   DFS / BFS

#### Cheatsheet

``` python
# Array / String traversal
for x in arr:
    ...

# Linked List Traversal
node = head
while node:
    ...
    node = node.next

# Hashing basics (set)
seen = set()
if x in seen:
    ...
seen.add(x)

# Two pointers (for sorted arrays / palindromes)
l, r = 0, len(arr)-1
while l < r:
    ...

# Sliding window (longest / shortest substring/subarray)
l = 0
for r in range(len(s)):
    ...
    while window_invalid():
        l += 1

# Frequency map (hash map)
freq = {}
for x in arr:
    freq[x] = freq.get(x, 0) + 1

# complement pattern (hash map)
index_map = {}   # value -> index
for i, x in enumerate(arr):
    comp = target - x
    if comp in index_map:
        return [index_map[comp], i]
    ...

# Prefix sums (range sum queries)
prefix = [0] * (n+1)
for i in range(n):
    prefix[i+1] = prefix[i] + arr[i]
# sum(l..r) = prefix[r+1] - prefix[l]

# Binary search (on sorted arrays or answer space)
l, r = 0, n-1
while l <= r:
    mid = (l+r)//2
    if good(mid):
        r = mid - 1
    else:
        l = mid + 1

# BFS / DFS (graph / tree traversal)

```

