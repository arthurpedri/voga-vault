## Iterator Protocol
- ==iter()== calls the .\_\_iter\_\_() method on the iterable, returning an iterator object.
- ==next()== calls the .\_\_next\_\_() method on the iterator, when all items have been iterated, raises StopIteration exception.

```python
iterator_obj = iter(iterable) # calls the .__iter__() method on the iterable, returning an iterator object
next(iterator_obj) 
```

- ==for loops== will call iter() on the iterable, and then next() until the StopIteration exception is raised.
### Custom iterators

```python
class FishInventory:
  def __init__(self, fishList):
      self.available_fish = fishList

  def __iter__(self):
    self.index = 0
    return self

  def __next__(self):
    if self.index < len(self.available_fish):
	    fish_status = self.available_fish[self.index] + " is available!"
        self.index += 1
        return fish_status
    else:
        raise StopIteration
```

## Built-in Iterators
```python
import itertools 
```

## Infinite iterators

```python
itertools.count(start=0, step=2) # infinite counter
```

## Input-dependent iterators
- Combines iterables into a single iterator.
```python
odd = [5, 7, 9]
even = {6, 8, 10}
all_numbers = itertools.chain(odd, even) 
```
## Combinatoric iterators
```python
even = [2, 4, 6]
even_combinations = list(itertools.combinations(even, 2)) # all combinations of 2 even numbers as tuples
```
  
## Enumerate zip, etc.

```python
for index, element in enumerate(my_list):
    pass
```
- Zip will create an iterator with tuples that share the same index based on the iterators given.
```python
numbers = [1, 2, 3]
letters = ['a', 'b', 'c']
zipped = zip(numbers, letters)
zipped  # Holds an iterator object
type(zipped) # <class 'zip'>
list(zipped) # [(1, 'a'), (2, 'b'), (3, 'c')]
```

## Generators

- Generator objects can be looped but the contents are not stored in memory.
- Great for complex and infinite iterations and streams of data.
- Generator functions must return an iterator using yield.
- Code after the yield will execute on the next iteration of the iterator.
```python
def course_generator():
    yield 'Computer Science' # yield will suspend the execution and preserve local variables
    yield 'Art'
    yield 'Business'

courses = course_generator()
for course in courses:
    print(course) # Will print each of the courses once
```
- Generators work with next() and raise StopIteration.