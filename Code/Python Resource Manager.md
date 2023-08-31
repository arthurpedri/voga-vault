****In python, resource managers are often used with the `with` keyword.
```python
with open("file_name.txt", "w") as file:  
   file.write("How you gonna win when you ain't right within?")
```
1. The `with` statement calls `open()`.
2. The `as` statement assigns the opened object to the variable file.
3. `write()` writes the sentence to the file.
```python
file = open("file_name.txt", "w")  
try:  
   file.write("How you gonna win when you ain't right within?")  
finally:  
   file.close()
```
The equivalent code needs to make sure to close the resource it opened, but using the resource manager we don't have to worry about forgetting to close opened resources.
## Class based context managers
A context manager class needs two methods explicitly defined:
1. `__enter__()` allows for the setup of context managers. Commonly takes care of opening resources and beginning the runtime context.
2. `__exit__()` ensures the breakdown of the context manager and handles exceptions. Commonly takes care of closing open resources that are no longer in use. 
```python
class WorkWithFile:  
  def __init__(self, file, mode):  
    self.file = file  
    self.mode = mode  
  
  def __enter__(self):  
    self.opened_file = open(self.file, self.mode)  
    return self.opened_file  
  
  def __exit__(self, *exc):  
    # Code to handle exceptions would go here
    self.opened_file.close()
```
## Contextlib
```python
from contextlib import contextmanager  
  
@contextmanager  
def open_file_contextlib(file, mode):  
    opened_file = open(file, mode)  
try:  
    yield opened_file  
finally:  
    opened_file.close()

with open_file_contextlib('file.txt', 'w') as opened_file:  
    opened_file.write('We just made a context manager using contexlib')
```
