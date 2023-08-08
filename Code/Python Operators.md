## Basic Operators
```python
x = 4
y = 3
x ** y # returns 64
x / y  # returns 1.333
x // y # returns 1 (Floor Division)
x % y # returns 1
x *= 4  # x is 16
x /= 4  # x is 1.0
x %= 4  # x is 0
```

## Slice Operator
```python
list[0, 1, 2]
list[::] == list(slice(0,len[list],1)) # slice operator works just like slice function
```

## Unpacking operator 
If a function expects arguments with the same name as keys on a dictionary, [[Python Functions#Multiple arguments|**kwargs]]  will take the correct values from those keys
```python
a, *b, c = [3, 6, 9, 12, 15] # output print(b): [6, 9, 12] | print(a): 3
my_tuple = (3, 6, 9)
merged_tuple = (0, *my_tuple, 12) # output: (0, 3, 6, 9, 12)
```

## Identity Operator
Used to compare objects, not if they are equal, but if they are actually the ==same object, with the same memory location==.
```python
if b is None:
        b = []
```

## Membership Operator
Used to test if a sequence ==is present== in an object.
```python
if (x in y):
    # returns true if x is in y
```