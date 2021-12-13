# Nuwa_framework
A deep learning framework powered by Zixing by using only numpy. 

In the folder, you'll find:
<br>
<br>
  **1 Nuwa.ipynb:** A demo contains all the module of Nuwa framework, it contains 4 main parts of which the architecture will be represent later. It also provide a testing set, 
  you could try your own dataset following the guide.
<br>  
  **2 Nuwa v0.0.1.png:** Nuwa v0.0.1's architecture, **Black bold** unit represents it's a python class while green dashed line represents the relationship between these classes. For       example, **Dataset** class parse the dataset to **NN**. Details are in the following section.

## <div align="center">Architecture</div>
The Nuwa framework consists of four parts in total: **Dataset**, **NN**, **Optimizer** and **Visual**. **Dataset** is responsible for dataset allocation, pre-processing and IO, **NN** contains different kinds of neural network layer such as fully connected layer, convolution layer etc, it also provide activation functions, it could be aclass which inherite Layer class, or it can be contained in other layers like fully connected layer and be calculated at the end of layer. **Optimizer** is a kind of "kernel" function of Nuwa. Inside, it provides optimizers like gradient descent and SGD, also it provides training function for training and calculate backpropagation by using dynamic computation graphe, each node in the graph is a **Node** type. It enables chain rule calculation be more efficient. You can always moniter gradient flow to check if there is gradient vanish during training. At last, **Visual** provides a series graph tool for plotting loss list or the gradient flow.

## <div align="center">Dataset class</div>
We assume that X is the feature training data and y its respecting label, they have same lines and can be concatenated by their axis 1. Also you can distribute dataset into training and test dataset by certain given proportion. During the mini batch graident descent training, it can also provide mini batchs by using builtin function getminiset()

## <div align="center">NN class</div>
NN simply represents "neural network". Since we have initialized dataset, we take it as variable and parse it in **NN** class. With the help of Layer class defined by NN, we can create a deep learning network like in the demo:

layer_list = [NN.Layer('Linear',3,10,'LeakyReLU'),NN.Layer('Linear',10,3,'LeakyReLU'), NN.Layer('Linear',3,1,'none')]

here take linear layer as example, **Layer** class takes type, input_dim, output_dim and activation as params, one can also use 

LinearLayer(input_dim, output_dim) 

to initialize a linear layer, defaultly, type equals 'Linear' and activation is None.
These two methods are exactly the same except the latter automatically set the layer type as linear.

ActivationFunc is a class which contains several static activation function methods: sigmoid, ReLU, LeakyReLU, tanh or none. it takes features from the last layer. You also have two methods to use activation functions. One is define inside **Layer** class. Or, **NN** provide activation function as **Layer**.

## <div align="center">Optimizer class</div>
**Optimizer** is the most important class in the architecture of Nuwa, as the training process and testing process are provided by it:

1 loss function

2 train(): including forword propagation and backpropagation

3 **Node** class allows every calculation in the backpropagation can be updated. 

4 lists: gradient list, weights list, loss list and passer list. All the list is accessible during model training

## <div align="center">Visual class</div>
Version 0.0.1 provides plotloss() and plotgradientnorm() to plot loss flow and gradient flow. More plots available in very soon
