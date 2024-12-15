# Neural Networks design notes

Designing a neural network requests the data scientist to make multiple choices: design of the layers, choice of the activation functions, hyper parameters...<br>
This guide is a collection of reflection on the subject in order to give the reader a simple guide to follow.

Some of the tips have been extracted from this article: https://towardsdatascience.com/designing-your-neural-networks-a5e4617027ed

In tensorflow/keras, you can create a neural network model using the Sequential function

```
from tensorflow.keras import Sequential

model = Sequential()
```

## Design of the layers

In tensorflow/keras, the simplest layer to add is a Dense layer. This is a fully connected one (all neurons are connected).

```
from tensorflow.keras.layers import Dense

model.add(Dense(name="test", inputs=64, activation="relu")
```

### Input layer

The number of neurons in the input layers is directly linked to the number of features you have in your dataset.<br>
If the dataset is tabular, it represents the number of columns.<br>
If the dataset is an inamge, you need to flatten it into a vector. Then the number of neurons is the size of the vector.<br>

### Output layer

The output layer will depend on the type task at hand.

#### Regression task

For a regression, generally the number of output will be set to 1 (what you are trying to predict). You might also try to do multi variate regression. In this case, you will have 1 neuron by variate.

#### Classification task

For classification, once again the design will be dependent on the task.

##### Binary classification

For this task, you have 2 classes. But as one is dependent on the other (if X is not of class A, it has to be of class B), you will need only 1 neuron, which represent either class A or class B (as you wish).

##### Multi class classification

Now, as you have many classes, you can't have a direct fallover. So you will need as many neurons as classes you are trying to predict.

##### Multi label classification

In case of multi lable classification, the choice is similat to multi class classification. In this case, the X you are trying to predict can be of multi classes. The only difference will be the choice of the activation function.

### Hidden layer

There are no rules for the hidden layers. You can only follow conventions that seem to work well in practice:
- 1 to 5 hidden layers seem to work well in practice
- 1 to 100 neurons by layers seem to be a standard (there is generally more improvements by adding hidden layers than adding more neurons)
- each hidden layers have generally the same number of neurons. When the input layer is large, you can have a first large hidden layer followed by smaller ones.

### Activation functions

The activation functions will depend on the task you are trying to achieve:

- **Regression:** 
- **Binary Classification:** You are trying to decide one class out of 2. You need to determine a probability of being in one of those class. Sigmoid activation function seems a good choice.
- **Multi class classifcation:** Your target is to determine one class out of N. The sum of probability for all classes should be 1. Under those constrains, the only activation function you can use is softmax.
- **Multi label classification:** In this case, the sum of probablity should not be equal to 1. You are trying to decide if your input is from any of the classes of choice. In this case, you cannot use softmax, so you will use the sigmoid activation function.

### Loss functions

As for the activation function, the choice of the loss function is dependent of the task:

- **Regression:** The standard choice is the MSE (Mean Root Squared Error). If there are outliers, you can use MAE (Mean Absolute Error) or the Huber loss.
  ```
  from tensorflow.keras.losses import MeanSquaredError, AbsolulteMeanError, Huber
  ```
- **Binary Classification:** For classification tasks, the cross entropy error is the by default choice. In the case of binary classification, you use the Binary Cross Entropy.
  ```
  from tensorflow.keras.losses import BinaryCrossEntropy
  ```
- **Classification**: In this case, you will chose the Cross Entropy. 
