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



