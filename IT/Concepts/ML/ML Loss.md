- Describes how wrong a model's predictions are
- Measures **distance**(not direction) between the model's predictions and the actual labels
- The goal of training a model is to minimize the loss
### Calculating loss
- The two most common methods are:
    1. Absolute of the difference (L1)
    2. Square of the difference (L2)
        - The square will make small differences even smaller and large differences larger
- Mean absolute error (MAE) and Mean squared error (MSE) are the average of the losses across a set of examples
- When processing multiple examples averaging is recommended across all examples
### Choosing a loss
Consider how you want the model to treat outliers:
- **MAE**. The model is further away from the outliers but closer to most of the other data points.
- **MSE**. The model is closer to the outliers but further away from most of the other data points.
The choice of loss depends on the importance of outliers in the data
