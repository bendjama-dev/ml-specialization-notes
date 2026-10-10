# Week 2: Neural Network training

## Video 2.1: Training a Neural Network

### Key Concepts

* **Three-Step TensorFlow Process**: Training a neural network involves specifying the model architecture, compiling it with a loss function, and fitting it to the training data.
* **Binary Crossentropy**: A loss function used during model compilation specifically tailored for binary classification tasks.
* **Epochs**: A technical term representing the total number of steps or iterations of the learning algorithm (such as gradient descent) run during training.

### Topics Covered

* Introduction to training neural networks using TensorFlow with a handwritten digit recognition example.
* Step 1: Model specification and layer configuration (hidden layers with 25 and 15 units using sigmoid activations, followed by an output unit).
* Step 2: Model compilation with a designated loss function.
* Step 3: Model training via the `.fit()` method over a set number of epochs.

### TensorFlow Training Pipeline Summary

* **Step 1: Model Specification**
* Strings together layers sequentially to define how inference is computed.


* **Step 2: Model Compilation**
* Configures the model by setting up the optimizer and selecting the loss function (e.g., binary crossentropy).


* **Step 3: Model Fitting**
* Executes the training process on input data $X$ and target labels $Y$ using the `.fit()` function.



### Notes

* Developing a conceptual mental model of what happens behind the code lines is essential for effective debugging when machine learning models fail to perform as expected.
* The upcoming videos will explore the internal mechanics of these TensorFlow steps in greater detail.

## Video 2.2: Details of Neural Network Training

### Key Concepts

* **Three-Step Framework**: Neural network training mirrors logistic regression through three core phases: specifying the architecture and inference computation, defining loss and cost functions, and minimizing the cost function.
* **Binary Crossentropy**: The standard loss function used for binary classification tasks (such as handwritten digit recognition of zeros and ones), penalizing incorrect probability predictions.
* **Mean Squared Error (MSE)**: An alternative loss function utilized when solving regression tasks rather than classification.
* **Backpropagation**: The standard algorithm used behind the scenes by deep learning frameworks to compute partial derivatives of the cost function with respect to every network parameter.

### Topics Covered

* Detailed mapping between logistic regression training steps and neural network training steps.
* Breakdown of TensorFlow model compilation using binary crossentropy and mean squared error loss functions.
* How TensorFlow's `.fit()` function handles parameter optimization over specified epochs.
* The evolution of software engineering practices in machine learning from custom scratch implementations to utilizing mature deep learning libraries like TensorFlow and Keras.

### Training Steps Summary

* **Step 1: Specify Computation and Architecture**
* Defines network layers, units, and activations (e.g., hidden layers with 25 and 15 units, output unit with sigmoid activation), establishing how inference and forward propagation are computed.


* **Step 2: Specify Loss and Cost Functions**
* Compiles the model with a loss function (e.g., binary cross-entropy for classification or MSE for regression). The overall cost function $J(\mathbf{W}, \mathbf{b})$ is computed as the average loss across all $m$ training examples.


* **Step 3: Minimize Cost Function**
* Optimizes all weights and biases across every layer using gradient descent, powered automatically by backpropagation during model fitting (`model.fit`).



### Notes

* Understanding the internal mechanics of training (forward propagation, loss computation, and backpropagation) provides a crucial conceptual mental model for debugging when models fail to perform as expected.
* While modern engineers rely heavily on mature libraries like TensorFlow and PyTorch rather than writing custom code from scratch, core theoretical knowledge remains essential for troubleshooting.
* The next video will explore alternative activation functions to replace the standard sigmoid function and enhance neural network performance.

## Video 2.3: Alternative Activation Functions

### Key Concepts

* **Rectified Linear Unit (ReLU)**: An activation function defined as $g(z) = \max(0, z)$, which outputs $0$ for negative inputs and passes positive values unchanged, allowing activations to take on any non-negative value.
* **Linear Activation Function**: An activation function defined as $g(z) = z$ (effectively behaving as if no activation function is applied).
* **Activation Function Choices**: The flexibility to use different mathematical functions per layer to model continuous, non-binary phenomena (such as customer awareness levels).

### Topics Covered

* Limitations of binary/sigmoid activations for continuous, non-negative quantities (e.g., measuring buyer awareness from zero to very large values)
* Definition, mathematical formula, and graphical shape of the ReLU activation function
* Overview of the three primary activation functions: Sigmoid, ReLU, and Linear

### Common Activation Functions Compared

* **Sigmoid Activation Function**
* **Formula**: $g(z) = \frac{1}{1 + e^{-z}}$
* **Range**: Strictly between $0$ and $1$.
* **Use Case**: Best for binary classification output layers where predictions represent probabilities.


* **ReLU (Rectified Linear Unit)**
* **Formula**: $g(z) = \max(0, z)$
* **Range**: $0$ to positive infinity ($[0, \infty)$).
* **Use Case**: Highly popular choice for hidden layers because it avoids flattening out for large positive values, speeding up training.


* **Linear Activation Function**
* **Formula**: $g(z) = z$
* **Range**: Negative infinity to positive infinity ($-\infty$ to $+\infty$).
* **Use Case**: Sometimes used in output layers for regression tasks when predicted values can be negative or arbitrarily large.



### Notes

* The term "ReLU" stands for Rectified Linear Unit, a historical naming convention from deep learning literature.
* Using alternative activation functions like ReLU allows neural networks to model diverse types of data distributions beyond strict $0$ to $1$ probabilities.
* The next video will discuss how to choose between these different activation functions for hidden layers versus output layers.
