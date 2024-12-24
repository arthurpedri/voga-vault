Datasets are made up of individual example that contain [[ML Feature|features]] and a [[ML Label|label]]
- Examples that contain both features and a label are called *labeled examples*
![[featuresandlabel.png]]

## Characteristics
A dataset might contain 100 years worth of data, but only for the month of July. Using this dataset to predict rainfall in January would produce poor predictions. Conversely, a dataset might cover only a few years but contain every month. This dataset might produce poor predictions because it doesn't contain enough years to account for variability.
- Good datasets are both large and highly diverse
### Size
Number of examples
### Diversity
The range the examples cover

### Number of features
- Datasets with more features can help a model discover additional patterns and make better predictions
- Although they don't _always_ produce models that make better predictions because some features might have no causal relationship to the label