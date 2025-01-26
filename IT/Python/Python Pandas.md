A DataFrame is similar to an in-memory spreadsheet. Like a spreadsheet:
- A DataFrame stores data in cells.
- A DataFrame has named columns (usually) and numbered rows.
```python
import pandas as pd
```
## Creating a DataFrame

The following code cell creates a simple DataFrame containing 10 cells organized as follows:

- 5 rows
- 2 columns, one named `temperature` and the other named `activity`

The following code cell instantiates a `pd.DataFrame` class to generate a DataFrame. The class takes two arguments:

- The first argument provides the data to populate the 10 cells. The code cell calls `np.array` to generate the 5x2 NumPy array.
- The second argument identifies the names of the two columns.

```python
# Create and populate a 5x2 NumPy array.
my_data = np.array([[0, 3], [10, 7], [20, 9], [30, 14], [40, 15]])

# Create a Python list that holds the names of the two columns.
my_column_names = ['temperature', 'activity']

# Create a DataFrame.
my_dataframe = pd.DataFrame(data=my_data, columns=my_column_names)
```
## Adding a new column to a DataFrame

You may add a new column to an existing pandas DataFrame just by assigning values to a new column name. For example, the following code creates a third column named `adjusted` in `my_dataframe`:
```python
# Create a new column named adjusted.
my_dataframe["adjusted"] = my_dataframe["activity"] + 2
```

## Specifying a subset of a DataFrame

Pandas provide multiples ways to isolate specific rows, columns, slices or cells in a DataFrame.
```python
print("Rows #0, #1, and #2:")
print(my_dataframe.head(3), '\n')

print("Row #2:")
print(my_dataframe.iloc[[2]], '\n')

print("Rows #1, #2, and #3:")
print(my_dataframe[1:4], '\n')

print("Column 'temperature':")
print(my_dataframe['temperature'])
```

## Copying a DataFrame (optional)

Pandas provides two different ways to duplicate a DataFrame:
- **Referencing.** If you assign a DataFrame to a new variable, any change to the DataFrame or to the new variable will be reflected in the other.
- **Copying.** If you call the `pd.DataFrame.copy` method, you create a true independent copy. Changes to the original DataFrame or to the copy will not be reflected in the other.
