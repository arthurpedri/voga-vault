- Python library for creating and manipulating matrices.
- Python calls matrices _lists_, NumPy calls them _arrays_ and TensorFlow calls them _tensors_. Python represents matrices with the [list data type](https://www.google.com/url?q=https%3A%2F%2Fdocs.python.org%2F3%2Flibrary%2Fstdtypes.html%23lists)
## Import
```python
import numpy as np
```
## Populate arrays with specific numbers
Call `np.array` to create a NumPy array with your own hand-picked values. For example, the following call to `np.array` creates an 8-element array:
```python
sequence_of_integers = np.arange(5, 12)
```
- Notice that `np.arange` generates a sequence that includes the lower bound (5) but not the upper bound (12).
## Populate arrays with random numbers

NumPy provides various functions to populate arrays with random numbers across certain ranges. For example, `np.random.randint` generates random integers between a low and high value. The following call populates a 6-element array with random integers between 50 and 100.
```python
random_integers_between_50_and_100 = np.random.randint(low=50, high=101, size=(6,))
```
Note that the highest generated integer `np.random.randint` is one less than the `high` argument.

To create random floating-point values between 0.0 and 1.0, call `np.random.random`. For example:
```python
random_floats_between_0_and_1 = np.random.random((6,))
```
## Mathematical Operations on NumPy Operands

If you want to add or subtract two arrays, linear algebra requires that the two operands have the same dimensions. Furthermore, if you want to multiply two arrays, linear algebra imposes strict rules on the dimensional compatibility of operands. Fortunately, NumPy uses a trick called [**broadcasting**](https://developers.google.com/machine-learning/glossary/#broadcasting) to virtually expand the smaller operand to dimensions compatible for linear algebra. For example, the following operation uses broadcasting to add 2.0 to the value of every item in the array created in the previous code cell:
```python
random_floats_between_2_and_3 = random_floats_between_0_and_1 + 2.0
```
The following operation also relies on broadcasting to multiply each cell in an array by 3:
```python
random_integers_between_150_and_300 = random_integers_between_50_and_100 * 3
```