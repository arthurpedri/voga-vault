## Exceptions are runtime errors, not syntax errors

```python
raise TypeError # Alternatives: raise TypeError() or TypeError('Message')
```

## Exception handling
- In case of exceptions: ==try > except > ... > except > finally==
- Without exceptions: ==try > else > finally==
- Most of the steps can be skipped, but if they are present, the order is set.
- It's good practice to predict possible exceptions and capture them specifically instead of capturing any exception.

```python
try:
    # code will always execute
    print(undefined_var)
except NameError as errorObject: # `as` allows us to capture the exception object
    # if an exception occurs in the try block, the exception will not block execution and will instead run the except block
    print('We hit a NameError')
    print(errorObject)
except KeyError:
    # multiple types of exception can be caught
    pass
except Exception: # python will execute the first except block that matches, so we can use generic exception as a backup
    pass
else:
    # else block executes after try block if no exception was encountered
    pass
finally:
    # will always occur at the end, regardless of exception or not
    pass
```
## User-defined exceptions
- Custom exceptions will appear on traceback, so they can be very useful.
```python
class LocationTooFarError(Exception): 
   def __init__(self, distance):
       self.distance = distance

   def __str__(self):
        return 'Location is not within 10 km: ' + str(self.distance)

raise LocationTooFarError(20)
```
