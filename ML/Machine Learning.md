Machine learning is the process of training a piece of software, called a [[ML Model|model]], to make useful [[ML Prediction|predictions]] or generate content from data.
- For example, modelling enormous amounts of weather data to learn the mathematical relationships instead of coding physics and math to represent the Earth's atmosphere and surface to compute the probability of rain

# Types of ML Systems
## Supervised learning
- These models make predictions after seeing lots of data with the correct answers an discovering the connections that produce the correct answers.

Two of the most common cases are regression and classification
### Regression
- Predicts a numeric value, for example future house price or amount of rain in milimetres.
### Classification
- Predicts the likelihood that something belongs to a category
- Divided into two groups, ==binary== and ==multiclass==, which differ by the number of possible classifications possible (binary being two)

## Unsupervised learning
- These models make predictions by being given data that does not contain any correct answers
### Clustering
- A commonly used technique that finds data points that demarcate natural grouping
- They differ from classification because the **categories aren't defined**

## Reinforcement learning
- They make predictions by getting rewards or penalties based on actions performed
- Generates a policy that defines the best strategy for getting the most rewards
- Useful for training robots to perform tasks and software to play games for example

## Generative AI
- A class of models that creates content from user input
- Examples are text-to-text, text-to-image, etc..
- They learn patterns in data with the goal to produce new but similar data
- Usually initially trained using an unsupervised approach to mimic the data it's trained on, further training may include supervised or reinforcement learning on specific data related to the tasks the model might be asked to perform