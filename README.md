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


### Common Patterns Cheatsheet Snippets

### **Array / String Traversal**
- Iterate through elements
```python
for x in arr:
    # process x
    ...
```

### **Linked List Traversal**
- Iterate through nodes
```python
node = head
while node:
    # process node.val
    ...
    node = node.next
```

### **Hashing Basics (Set / Dict)**
- Track seen elements or frequency
```python
# Set
seen = set()
if x in seen:
    ...
seen.add(x)

# Frequency Map
freq = {}
for x in arr:
    freq[x] = freq.get(x, 0) + 1
```

### **Complement Pattern (Two Sum)**
- Use hash map for value -> index lookup
```python
index_map = {}  # value -> index
for i, x in enumerate(arr):
    comp = target - x
    if comp in index_map:
        return [index_map[comp], i]
    index_map[x] = i
```

### **Two Pointers**
- For sorted arrays, palindromes, or window problems
```python
l, r = 0, len(arr)-1
while l < r:
    # process arr[l], arr[r]
    ...
    l += 1
    r -= 1
```

### **Sliding Window**
- For longest/shortest substring/subarray problems
```python
l = 0
for r in range(len(s)):
    # add s[r] to window
    ...
    while window_invalid():
        # remove s[l] from window
        l += 1
```

### **Prefix Sums**
- Compute range sums efficiently
```python
prefix = [0]*(n+1)
for i in range(n):
    prefix[i+1] = prefix[i] + arr[i]
# sum of range l..r = prefix[r+1] - prefix[l]
```

### **Binary Search**
- Standard search template
```python
l, r = 0, n-1
while l <= r:
    mid = (l+r)//2
    if good(mid):
        r = mid - 1
    else:
        l = mid + 1
```

### **DFS / BFS**
- Graph or tree traversal
```python
# BFS
from collections import deque
queue = deque([start])
visited = set([start])
while queue:
    node = queue.popleft()
    for nei in graph[node]:
        if nei not in visited:
            visited.add(nei)
            queue.append(nei)

# DFS
def dfs(node):
    visited.add(node)
    for nei in graph[node]:
        if nei not in visited:
            dfs(nei)
```


## Design Patterns

### **Singleton**
- **Purpose**: Ensure a class has only one instance and provide a global access point.
- **Use When**: You need exactly one shared resource (e.g., configuration manager, logging service).
- **Key Idea**: Private constructor + static instance accessor.
- **Code Example (Python)**:
```python
class Singleton:
    _instance = None

    def __new__(cls, *args, **kwargs):
        if not cls._instance:
            cls._instance = super().__new__(cls, *args, **kwargs)
        return cls._instance

singleton1 = Singleton()
singleton2 = Singleton()
print(singleton1 is singleton2)  # True
```

---

### **Factory**
- **Purpose**: Decouple object creation from the concrete implementation.
- **Use When**: You want flexibility in creating objects without exposing creation logic.
- **Key Idea**: Use factory classes or methods to create objects.
- **Code Example (Python)**:
```python
class Dog:
    def speak(self):
        return 'Woof'

class Cat:
    def speak(self):
        return 'Meow'

class AnimalFactory:
    @staticmethod
    def create_animal(animal_type):
        if animal_type == 'dog':
            return Dog()
        elif animal_type == 'cat':
            return Cat()

animal = AnimalFactory.create_animal('dog')
print(animal.speak())  # Woof
```

---

### **Observer**
- **Purpose**: Enable reactive, event-driven communication between objects.
- **Use When**: One change should notify multiple dependent objects.
- **Key Idea**: Subject maintains a list of observers and notifies them automatically.
- **Code Example (Python)**:
```python
class Subject:
    def __init__(self):
        self._observers = []

    def attach(self, observer):
        self._observers.append(observer)

    def notify(self, message):
        for observer in self._observers:
            observer.update(message)

class Observer:
    def update(self, message):
        print(f'Received: {message}')

subject = Subject()
obs1 = Observer()
obs2 = Observer()
subject.attach(obs1)
subject.attach(obs2)
subject.notify('Event occurred!')
```

---

### **Strategy**
- **Purpose**: Encapsulate interchangeable algorithms or behaviors.
- **Use When**: You want to swap algorithms at runtime.
- **Key Idea**: Define a family of algorithms and make them interchangeable via a common interface.
- **Code Example (Python)**:
```python
class StrategyA:
    def execute(self, data):
        return f'Processing {data} with StrategyA'

class StrategyB:
    def execute(self, data):
        return f'Processing {data} with StrategyB'

class Context:
    def __init__(self, strategy):
        self.strategy = strategy

    def set_strategy(self, strategy):
        self.strategy = strategy

    def do_task(self, data):
        return self.strategy.execute(data)

context = Context(StrategyA())
print(context.do_task('input'))  # StrategyA
context.set_strategy(StrategyB())
print(context.do_task('input'))  # StrategyB
```

---

### **Decorator**
- **Purpose**: Dynamically add responsibilities or features to objects.
- **Use When**: You want flexible, on-demand extension instead of subclass explosion.
- **Key Idea**: Wrap an object with another object implementing the same interface.
- **Code Example (Python)**:
```python
class Component:
    def operation(self):
        return 'Base Operation'

class Decorator:
    def __init__(self, component):
        self.component = component

    def operation(self):
        return f'Decorated({self.component.operation()})'

component = Component()
decorated = Decorator(component)
print(decorated.operation())  # Decorated(Base Operation)
```








