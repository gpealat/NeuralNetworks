# Neural Networks design notes

## Input layer

The number of neurons in the input layers is directly linked to the number of features you have in your dataset.
If the dataset is tabular, it represents the number of columns.
If the dataset is an inamge, you need to flatten it into a vector. Then the number of neurons is the size of the vector.

## Hidden layer

## Output layer

The output layer will depend on the type task at hand.

### Regression task

For a regression, generally the number of output will be set to 1 (what you are trying to predict). You might also try to do multi variate regression. In this case, you will have 1 neuron by variate.

### Classification task
