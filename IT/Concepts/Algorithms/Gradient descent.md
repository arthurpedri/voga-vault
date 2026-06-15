Mathematical technique that iteratively finds the weights and bias that produce the model with the lowest [[ML Loss|loss]] 
## Rough algorithm
1. Calculate the loss with the current weight and bias
2. Determine the direction to move the weights and bias that reduce loss
3. Move the weight and bias values a small amount([[Hyperparameters#Learning rate|learning rate]]) in the direction that reduces loss
4. Return to step one until the model can't reduce loss any further

## Convergence and convex functions
- The loss functions for linear models always produce a convex surface, as a result of this property, when a linear regression model converges, we know the model has found the weights and bias that produce the lowest loss
![[gradientdescentconverging.png]]
- Note that **the model almost never finds the exact minimum for each weight and bias**, but instead finds a value very close to it

## Stochastic gradient descent (SGD)
- Uses only a single example ([[Hyperparameters#Batch size|batch size]] of one) per iteration
- Given enough iterations, SGD works but is very [[ML Noise|noisy]]
- "Stochastic" indicates that the one example comprising each batch is chosen at random
## Mini-batch stochastic gradient descent (mini-batch SGD)
- Compromise between full-batch and SGD (1 < size < N)
- Model chooses examples included at random
- Determining the number of examples for each batch depends on the dataset and the available compute resources
- In general, small batch sizes behaves like SGD, and larger batch sizes behaves like full-batch gradient descent