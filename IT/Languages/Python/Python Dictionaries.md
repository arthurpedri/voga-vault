## Dictionaries
Key value pairs where the ==key must be an immutable data type== (number, string, tuple).
```python
shopping_list1 = {'jewelry': 'earrings', 'clothes': 'jeans', 'budget': 200}
shopping_list2 = {
    'shoes': 'sandals', 
    'budget': 350
}
shopping_list1.keys() # returns dict_keys(['jewelry', 'clothes', 'budget'])
shopping_list1.values() # returns dict_values(['earrings', 'jeans', 200])
shopping_list1.items() # returns both keys and values
shopping_list1.update(shopping_list2)
del shopping_list1["clothes"]
print(shopping_list1) # prints {'jewelry': 'earrings', 'clothes': 'jeans', 'budget': 350, 'shoes': 'sandal
```
