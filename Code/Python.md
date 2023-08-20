
## Conventions
- [[Pep8]]
- 4 spaces as indentation
```python
def function_name():
	variable_name = 1+1
	return variable_name
```

## Main 
Including the main() function allows us to use the functions and classes of the module elsewhere without running the "main code".
Placing the if statement in our program basically checks whether the program is being run independently as the primary module or as a library in another script
```python
if __name__ == '__main__':
    main()
```

## String Literals & Format Function
```python
print('Very nice to meet you, {}!'.format(name), f'from {name}!')
```

## Casting
```python
temperature = str(97.5)
type(temperature) # prints str
```

[[Python Operators|Operators]]

## Loops
```python
names = []
for name in names:
    if 'h' in name.lower():
        # break terminates the loop
        # continue skips over the iteration and goes to the next
        # pass does nothing
        break
```

##  Lists
```python
new_list = []
new_list.append("Hello, " + name) # also .pop and .remove
my_list = new_list[1:] # element at pos 1 until last element
range(0, len(my_list), 2) # starts at index 0 until len(my_list) non inclusive with a step of 2
```

[[Python Classes|Classes]]

## Strings
```python
str = "String"
# str.lower, .upper, .title, ...
len(str)
str.split("separator") # default separator is whitespace
```

## Tuples
A tuple is a collection that is ordered and ==immutable==.
They are more efficient than lists because of the immutability.
```python
tuple = (1, 'ab')
single_member_tuple = ('one',) # with a comma (otherwise python treats it as a parenthesis and doesn't create a tuple)
```

## Dictionaries
Key value pairs where the ==key must be an immutable data type== (number, string, tuple).
```python
shopping_list1 = {'jewelry': 'earrings', 'clothes': 'jeans', 'budget': 200}
shopping_list2 = {'shoes': 'sandals', 'budget': 350}
shopping_list1.keys() # returns dict_keys(['jewelry', 'clothes', 'budget'])
shopping_list1.values() # returns dict_values(['earrings', 'jeans', 200])
shopping_list1.items() # returns both keys and values
shopping_list1.update(shopping_list2)
print(shopping_list1) # prints {'jewelry': 'earrings', 'clothes': 'jeans', 'budget': 350, 'shoes': 'sandal
```

## [[Sets]]
```python
{value1, value2} # Set
set([1, 2, 2, 3]) # Will create a set based on the list (removing duplicates)
# Sets don't have indexes or keys, we can use in to check if something is in the set
# They are iterable
# functions .add(), .remove(), .update()
```

## [[Python Scope|Scope]]

## [[Python Exceptions|Exceptions]]

## [[Python Testing|Testing]]

## [[Python Iterables|Iterables]]

## [[Python Generators|Generators]]
