While parameters are the variables that are part of the model itself and are calculated during training, hyperparameters are values that you control

## Learning rate
A floating point number that influences how quickly the model converges
- If it is too low, the model can take a long time to converge
- If it is too high, the model never converges, but instead bounces around the weights and bias that minimize the loss
### Calculation
- The learning rate determines the magnitude of the changes made to the weights and bias during each step of the gradient descent process
- The model multiplies the gradient by the learning rate to determine the parameters for the next iteration

## Batch size
Refers to the number of examples the model processes before updating its weights and bias
- When a dataset contains too many examples, using the full batch isn't practical
Two common techniques to get the right gradient on average without needing to look at every example in the dataset are [[Gradient descent#Stochastic gradient descent (SGD)|SGD]] and [[Gradient descent#Mini-batch stochastic gradient descent (mini-batch SGD)|mini-batch SGD]]

## Epochs
During training, and epoch means that the model has processed every example in the training set *once*
- If training with a mini-batch size, the model will take multiple iterations to complete one epoch
- Training typically requires many epochs
- In general, more epochs produces a better model, but also takes more time to train