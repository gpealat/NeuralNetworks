# Neural Networks design notes

Designing a neural network requests the data scientist to make multiple choices: design of the layers, choice of the activation functions, hyper parameters...
This guide is a collection of reflection on the subject in order to give the reader a simple guide to follow.

## Input layer

The number of neurons in the input layers is directly linked to the number of features you have in your dataset.
If the dataset is tabular, it represents the number of columns.
If the dataset is an inamge, you need to flatten it into a vector. Then the number of neurons is the size of the vector.

## Output layer

The output layer will depend on the type task at hand.

### Regression task

For a regression, generally the number of output will be set to 1 (what you are trying to predict). You might also try to do multi variate regression. In this case, you will have 1 neuron by variate.

### Classification task

For classification, once again the design will be dependent on the task.

#### Binary classification

For this task, you have 2 classes. But as one is dependent on the other (if X is not of class A, it has to be of class B), you will need only 1 neuron, which represent either class A or class B (as you wish).

#### Multi class classification

Now, as you have many classes, you can't have a direct fallover. So you will need as many neurons as classes you are trying to predict.

#### Multi label classification

In case of multi lable classification, the choice is similat to multi class classification. In this case, the X you are trying to predict can be of multi classes. The only difference will be the choice of the activation function.

## Hidden layer

