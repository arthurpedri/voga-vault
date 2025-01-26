## [[Namespaces]]
- In python, namespaces are a dictionary with the name as keys and the objects they reference as values.

- Imports will make a new namespace and not add to the global namespace.

- Enclosing namespaces are created when we work with nested functions (the names in the enclosing functions are in the enclosing namespace).

## Scope defines which namespace our program will look into and in what order

### Built-in > Global > Enclosing(Nonlocal) > Local
### Scope Resolution: L > E > G > B, python will search for the name in order.

- While namespaces are storage for names, scopes are rules for which name to retrieve.

- Immutable objects can be accessed in nested functions, but cannot be modified (Unbound local error).

- Global scoped values can be accessed but not modified.

- Using the nonlocal statement, we can modify names inside nested functions.

```python
def enclosing_funtion():
    var = "value"
    
    def nested_function():
        nonlocal var
        global my_tuple # Global names can be modified using the global statement (similar to nonlocal)
        var = "new_value"
    print(var) # Will print new_value
```

- Global statement can be used even if the name has not been defined in the global namespace. Using it will create the new variable in the global namespace.

