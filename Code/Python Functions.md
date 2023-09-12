## Mutables as default arguments
The definition of a function will only be evaluated once, so anything instantiated in the definition will be reused on all calls.
We should use ==*None*== in the definition and instantiate the mutable inside the function using the [[Python Operators#Identity Operator|identity operator]].
```python
def foo(a, b = []): # This expression is evaluated only once and will use the same empty string for all calls                       
    b.append(a)

def bar(a,b = None): # The None workaround fixes this problem by instantiating the list after
    if b is None:
        b = []
    b.append(a)
```

## Multiple arguments

```python
def funct(positional_argument, *arguments): # Unpacking operator (*) stores arguments as a tuple
        # Positional arguments must come before variable arguments (SyntaxError)
    print(arguments)

def func2(**kwargs): # Keyword arguments, stores arguments as a dictionary
    print(kwargs.get('name'))
    
func2(key='value', key2=7) # how to pass the arguments with keys
# Order of arguments :  standard positional arguments, *args, standard keyword arguments, **kwargs
```

## Higher-order functions and lambda

```python
add_two = lambda x: x + 2
if_function = lambda num: 'big' if num > 100 else 'small'
```
- Functions are first class objects.
- First class objects can be stored as variables, passed as arguments, returned, stored in data structures.
- Higher order functions either take a function as argument or return a function.
- map(), filter(), reduce() are built-in higher order functions.

```python
returned_map_object = map(funct, b) # Applies funct to each element of the iterable b
list(returned_map_object) # will convert the map to a list

names = ["margarita", "Linda", "Masako", "Maki", "Angela"]
M_names = filter(lambda name: name[0] == "M" or name[0] == "m", names) # Similar to map, only elements evaluated to true are in the return

from functools import reduce # has to be imported to be used

int_list = [3, 6, 9, 12]

reduced_int_list = reduce(lambda x,y: x*y, int_list) # esentially does 3 * 6 = 18 * 9 = 162 * 12 = 1944
# returns a single value
``` 

## Decorators

- Decorator functions will add functionality to the parameter function and return a new combined function.
- Decorator will basically replace the syntax of: ==function_to_be_decorated = decorator_function(function_to_be_decorated)==

```python
def decorator_function(func):
    def wrapper(*args): # args have to be passed to use parameters
        print("Additional stuff ")
        func(*args)
        
    return wrapper
    
@decorator_function 
def function_to_be_decorated(name):
    print("Base stuff" + name)
    
function_to_be_decorated("art")
```

- Very useful for tracking time of a function and debugging functions, especially ones that are not yours, like std lib functions.

```python
import functools

def do_twice(func):
    @functools.wraps(func) # Preserves information about the original function, so that help and other commands can be used on the inner function
    def wrapper_do_twice(*args, **kwargs):
        func(*args, **kwargs)
        return func(*args, **kwargs) # Has to return a value, otherwise the decorated function will return None

    return wrapper_do_twice

@do_twice
def return_greeting(name):
    print("Creating greeting")
    return f"Hi {name}"
```

- Decorators don't have to wrap the function they're decorating, they can simply register it exists and return it unwrapped:

```python
PLUGINS = dict()

def register(func):
    """Register a function as a plug-in"""
    PLUGINS[func.__name__] = func
    return func # no need for @functools.wraps because you are returning the original function unmodified

@register
def say_hello(name):
    return f"Hello {name}"
```

  