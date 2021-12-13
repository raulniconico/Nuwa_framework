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

