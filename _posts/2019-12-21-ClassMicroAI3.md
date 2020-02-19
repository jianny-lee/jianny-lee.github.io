---
layout: post
title: "[Class] Micro - AI 특강 3,4일차"
date: 2019-12-21
categories: study
tags: machinelearning, deeplearning, microAI
comments: true
---

# Micro - AI 특강 Day 3

ESP32는 Bluetooth 기능을 갖고 있지만, wi-fi 기능은 갖고있지 않음
AI SW의 특징은 처리할 데이터가 많기 때문에 성능이 좋은 hardware를 사용해야 함
pc에 *flash하는 sw*를 설치해야 함

list는 다른 타입들이 들어와도 허용가능
또한 list내에 list를 추가하는 것도 가능

method overadding
: 중복되는 메소드를 제거하는 것
function을 이용하여 내용을 바꾸는 것을 encapsulation이라고 함. -> 이게 더 안전함

---
## [AI]
EBP  : Error BackPropagation
error란, 예상값(?)-출력값
epoch : 반복 횟수를 의미
학습을 계속 시키는 이유는, error를 낮추게 하기 위해서

python neural network[python neural network](https://towardsdatascience.com/inroduction-to-neural-networks-in-python-7e0b422e6c24)

학습이란 weight(가중치)를 찾기 위한 과정으로, error가 최소화 되는 직선을 찾기 위함

```python
from random import seed
from random import random

# Initialize a network
def initialize_network(n_inputs, n_hidden, n_outputs):
    network = list()
    hidden_layer = [{'weights':[random() for i in range(n_inputs + 1)]} for i in range(n_hidden)]
    network.append(hidden_layer)
    output_layer = [{'weights':[random() for i in range(n_hidden + 1)]} for i in range(n_outputs)]
    network.append(output_layer)
    return network

seed(1)
network = initialize_network(2, 1, 2) # weight list(matrix)
for layer in network:
    print(layer)

print()
print(network)
print()

###################### forward propagation(after learning) ##############
from math import exp

# Calculate neuron activation for an input
def activate(weights, inputs):
    activation = weights[-1]
    for i in range(len(weights)-1):
        activation += weights[i] * inputs[i]
    return activation

# Transfer neuron activation
def transfer(activation):
    return 1.0 / (1.0 + exp(-activation))

# Forward propagate input to a network output
def forward_propagate(network, row):
    inputs = row
    for layer in network:
        new_inputs = []
        for neuron in layer:
            activation = activate(neuron['weights'], inputs)
            neuron['output'] = transfer(activation)
            new_inputs.append(neuron['output'])
        inputs = new_inputs
    return inputs

# test forward propagation
network = [[{'weights': [0.13436424411240122, 0.8474337369372327, 0.763774618976614]}],
        [{'weights': [0.2550690257394217, 0.49543508709194095]}, {'weights': [0.4494910647887381, 0.651592972722763]}]]
print(network)
row = [1, 0, None]
output = forward_propagate(network, row)
print(network)
print(output)
print()


###################### forward/backward propagation(learning) ##############

# Calculate the derivative of an neuron output
def transfer_derivative(output):
    return output * (1.0 - output)

# Backpropagate error and store in neurons
def backward_propagate_error(network, expected):
    for i in reversed(range(len(network))):
        layer = network[i]
        errors = list()
        if i != len(network)-1:
            for j in range(len(layer)):
                error = 0.0
                for neuron in network[i + 1]:
                    error += (neuron['weights'][j] * neuron['delta'])
                errors.append(error)
        else:
            for j in range(len(layer)):
                neuron = layer[j]
                errors.append(expected[j] - neuron['output'])
        for j in range(len(layer)):
            neuron = layer[j]
            neuron['delta'] = errors[j] * transfer_derivative(neuron['output'])

# test backpropagation of error
network = [[{'output': 0.7105668883115941, 'weights': [0.13436424411240122, 0.8474337369372327, 0.763774618976614]}],
        [{'output': 0.6213859615555266, 'weights': [0.2550690257394217, 0.49543508709194095]}, {'output': 0.6573693455986976, 'weights': [0.4494910647887381, 0.651592972722763]}]]
expected = [0, 1]
print(network)
print()
backward_propagate_error(network, expected)
print(network)
print()
for layer in network:
    print(layer)

row = [1, 0, None]
output = forward_propagate(network, row)
print(network)
print(output)

###################### Final forward/backward propagation with dataset (learning-testing) ##############

from math import exp
from random import seed
from random import random

# Initialize a network
def initialize_network(n_inputs, n_hidden, n_outputs):
    network = list()
    hidden_layer = [{'weights':[random() for i in range(n_inputs + 1)]} for i in range(n_hidden)]
    network.append(hidden_layer)
    output_layer = [{'weights':[random() for i in range(n_hidden + 1)]} for i in range(n_outputs)]
    network.append(output_layer)
    return network

# Calculate neuron activation for an input
def activate(weights, inputs):
    activation = weights[-1]
    for i in range(len(weights)-1):
        activation += weights[i] * inputs[i]
    return activation

# Transfer neuron activation
def transfer(activation):
    return 1.0 / (1.0 + exp(-activation))

# Forward propagate input to a network output
def forward_propagate(network, row):
    inputs = row
    for layer in network:
        new_inputs = []
        for neuron in layer:
            activation = activate(neuron['weights'], inputs)
            neuron['output'] = transfer(activation)
            new_inputs.append(neuron['output'])
        inputs = new_inputs
    return inputs

# Calculate the derivative of an neuron output
def transfer_derivative(output):
    return output * (1.0 - output)

# Backpropagate error and store in neurons
def backward_propagate_error(network, expected):
    for i in reversed(range(len(network))):
        layer = network[i]
        errors = list()
        if i != len(network)-1:
            for j in range(len(layer)):
                error = 0.0
                for neuron in network[i + 1]:
                    error += (neuron['weights'][j] * neuron['delta'])
                errors.append(error)
        else:
            for j in range(len(layer)):
                neuron = layer[j]
                errors.append(expected[j] - neuron['output'])
        for j in range(len(layer)):
            neuron = layer[j]
            neuron['delta'] = errors[j] * transfer_derivative(neuron['output'])

# Update network weights with error
def update_weights(network, row, l_rate):
    for i in range(len(network)):
        inputs = row[:-1]
        if i != 0:
            inputs = [neuron['output'] for neuron in network[i - 1]]
        for neuron in network[i]:
            for j in range(len(inputs)):
                neuron['weights'][j] += l_rate * neuron['delta'] * inputs[j]
            neuron['weights'][-1] += l_rate * neuron['delta']

# Train a network for a fixed number of epochs
def train_network(network, train, l_rate, n_epoch, n_outputs):
    for epoch in range(n_epoch):
        sum_error = 0
        for row in train:
            outputs = forward_propagate(network, row)
            expected = [0 for i in range(n_outputs)]
            expected[row[-1]] = 1
            sum_error += sum([(expected[i]-outputs[i])**2 for i in range(len(expected))])
            backward_propagate_error(network, expected)
            update_weights(network, row, l_rate)
        print('< epoch=%d, learning_rate=%.3f, error=%.3f >' % (epoch, l_rate, sum_error))

# Test training backprop algorithm
seed(1)
dataset= [[2.7810836,2.550537003,0],
            [1.465489372,2.362125076,0],
            [3.396561688,4.400293529,0],
            [1.38807019,1.850220317,0],
            [3.06407232,3.005305973,0],
            [7.627531214,2.759262235,1],
            [5.332441248,2.088626775,1],
            [6.922596716,1.77106367,1],
            [8.675418651,-0.242068655,1],
            [7.673756466,3.508563011,1]]
n_inputs = len(dataset[0]) - 1
n_outputs = len(set([row[-1] for row in dataset])) #one-hot assignment
network = initialize_network(n_inputs, 2, n_outputs)
train_network(network, dataset, 0.5, 200, n_outputs)
for layer in network:
    print(layer)
    
for row in dataset:
    outputs = forward_propagate(network, row)
    print(row, outputs,)


###################### Final forward/backward propagation with dataset (learning-testing-prediction) ##############
    
from math import exp

# Calculate neuron activation for an input
def activate(weights, inputs):
    activation = weights[-1]
    for i in range(len(weights)-1):
        activation += weights[i] * inputs[i]
    return activation

# Transfer neuron activation
def transfer(activation):
    return 1.0 / (1.0 + exp(-activation))

# Forward propagate input to a network output
def forward_propagate(network, row):
    inputs = row
    for layer in network:
        new_inputs = []
        for neuron in layer:
            activation = activate(neuron['weights'], inputs)
            neuron['output'] = transfer(activation)
            new_inputs.append(neuron['output'])
        inputs = new_inputs
    return inputs

# Make a prediction with a network
def predict(network, row):
    outputs = forward_propagate(network, row)
    return outputs.index(max(outputs))

# Test making predictions with the network
dataset = [[2.7810836,2.550537003,0],
    [1.465489372,2.362125076,0],
    [3.396561688,4.400293529,0],
    [1.38807019,1.850220317,0],
    [3.06407232,3.005305973,0],
    [7.627531214,2.759262235,1],
    [5.332441248,2.088626775,1],
    [6.922596716,1.77106367,1],
    [8.675418651,-0.242068655,1],
    [7.673756466,3.508563011,1]]
network = [[{'weights': [-1.482313569067226, 1.8308790073202204, 1.078381922048799]}, {'weights': [0.23244990332399884, 0.3621998343835864, 0.40289821191094327]}],
    [{'weights': [2.5001872433501404, 0.7887233511355132, -1.1026649757805829]}, {'weights': [-2.429350576245497, 0.8357651039198697, 1.0699217181280656]}]]
for row in dataset:
    prediction = predict(network, row)
    print('Expected=%d, Got=%d' % (row[-1], prediction))
```
![aiclass_d01](https://user-images.githubusercontent.com/56791347/71303339-ba24ee00-23fa-11ea-8aa1-1c62b895a45a.PNG)
![aiclass_d02](https://user-images.githubusercontent.com/56791347/71303340-ba24ee00-23fa-11ea-8559-dc0f4d4aaa90.PNG)

---

# Micro - AI 특강 Day 4

**Perceptron**
-> node 하나가 입력을 받는 것
Supervising : 입력과 출력이 결정되어있는 것 -> 일반적으로 이것을 ‘학습한다’라고 함
unsupervising : 입력만 결정되어 있는 것

* Training, fit, learning, optimize : error가 발생하면, weight를 저장하며 계속 학습시켜 주는 것
	* 여기서 반복하는 횟수를 *epoch*이라고 함
	* activation function은 여러가지가 있음 -> 일반적으로 sigmoid 함수를 사용함
	* activation function을 잘 선택해야, weight update를 잘 할 수 있음
	* learning late : 학습률이라고 하며, 도출된 error를 얼마나 반영할 것인지에 대한 것
	* Forward Propagation : input을 넣으면 output이 나옴
	* Back Propagation : error용

// neural network = deep learning

학습시에는 초기값을 잘 정해야함. 그래서 초기값을 잘 정하면, 학습이 잘 된다.

————-
python은 기본적으로 list구조를 갖고있음. 일괄적인 처리를 못하기 때문에 array로 묶여있는데, 이를 numpy라고 함. 
tensor는 gpu에 기억될 수 있는 데이터 묶음

pytorch, tensorflow,pandas,sklearn module을 thonny에서 설치
MLP : multi layer perceptron 
x : input, y:output -> list로 구성되어 있음. 진리표를 list로 저장해놓음

1.학습 (딱 한번만 실행됨, 학습은 오래걸림 : forward(error를 찾는 것),backward가 구성되어 있어서)
2.prediction

---
example1

```python
import warnings
warnings.simplefilter("ignore")
from sklearn.neural_network import MLPClassifier
#data set
X = [[0., 0., 0., 1.], [0., 0., 1., 0.], [0., 1., 0., 0.],  [1., 0., 0., 0.]]
y = [[0, 0],[0, 1], [1, 0],[1, 1]]

#learning model
clf = MLPClassifier(solver='lbfgs', alpha=0.000001, hidden_layer_sizes=(4,7,6), random_state=100, activation='logistic', max_iter=200)
clf.fit(X, y)
print("------------------------------------------------------------")
print("Training loss = " + str(clf.loss_))
print()
print("Coefficients :")
print(clf.coefs_)
print()
print("Intercepts :")
print(clf.intercepts_)
print()
print("Predict for [[0., 0.], [0., 1.], [1., 0.],  [1., 1.]]")
print("Predicted value = "+ str(clf.predict([[0., 0., 0., 1.], [0., 0., 1., 0.], [0., 1., 0., 0.],  [1., 0., 0., 0.]])))
print("------------------------------------------------------------")
```

example2

```python
import numpy as np
from keras.models import Sequential
from keras.layers.core import Dense

# Traing Data
input_data = np.array([[0, 0], [0, 1], [1, 0], [1, 1]], "float32")

output_data = np.array([[0], [1], [1], [0]], "float32")

# Setting up the model
# Modeling ->  line connect automatically
# Weight is a learning result
model = Sequential()
model.add(Dense(16, input_dim=2, activation='sigmoid')) #using a 16 nodes
model.add(Dense(1, activation='sigmoid'))

# Training the model
model.compile(loss='mean_squared_error', optimizer='adam', metrics=['binary_accuracy'])
model.fit(input_data, output_data, nb_epoch=5000, verbose=2)

# Testing the model
print(model.predict(input_data).round())
```
![02](https://user-images.githubusercontent.com/56791347/71303365-feb08980-23fa-11ea-8774-1f39b8f7876f.PNG)

### [pytorch]
torch가 사용하는 array : torch.tensor
tensorflow : dataflow를 modeling하는 package 모음
```python
import torch 
import torch.nn as nn

# Defining input size, hidden layer size, output size and batch size respectively
n_in, n_h, n_out, batch_size = 10, 5, 1, 10

# Create dummy input and target tensors (data)
x = torch.randn(batch_size, n_in)
y = torch.tensor([[1.0], [0.0], [0.0], 
[1.0], [1.0], [1.0], [0.0], [0.0], [1.0], [1.0]])

# Create a model
model = nn.Sequential(nn.Linear(n_in, n_h),
   nn.ReLU(),
   nn.Linear(n_h, n_out),
   nn.Sigmoid())

# Construct the loss function
criterion = torch.nn.MSELoss()
# Construct the optimizer (Stochastic Gradient Descent in this case)
optimizer = torch.optim.SGD(model.parameters(), lr = 0.01)

# Gradient Descent
for epoch in range(10000):
   # Forward pass: Compute predicted y by passing x to the model
   y_pred = model(x)

   # Compute and print loss
   loss = criterion(y_pred, y)
   print('epoch: ', epoch,' loss: ', loss.item())

   # Zero gradients, perform a backward pass, and update the weights.
   optimizer.zero_grad()

   # perform a backward pass (backpropagation)
   loss.backward()

   # Update the parameters
   optimizer.step()
```

```python
#만약 module 'tensorflow' has no attribute 'matrix_determinant'라는 에러가 발생시 추가
import tensorflow.compat.v1 as tf
import numpy as np

tf.disable_v2_behavior()
```