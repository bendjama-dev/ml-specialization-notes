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

## Video 2.4: Choosing Activation Functions

### Key Concepts

* **Output Layer Activation Selection**: Choosing the activation function for the final layer based on the nature of the target variable $y$ (binary classification vs. regression tasks).
* **Hidden Layer Default Choice**: Using the **ReLU** activation function as the standard choice for hidden layers due to computational efficiency and mitigation of flat gradient regions.
* **TensorFlow Implementation**: Configuring specific activation functions per layer using parameters like `activation='relu'`, `activation='sigmoid'`, or `activation='linear'`.

### Topics Covered

* Guidelines for selecting output layer activation functions based on ground-truth labels ($y$)
* Why ReLU has become the dominant choice for hidden layers compared to historical sigmoid usage
* Overview of alternative advanced activation functions (LeakyReLU, tanh, swish)
* Introduction to the question of why activation functions are necessary in the first place

### Output Layer Activation Recommendations

* **Binary Classification ($y \in \{0, 1\}$)**
* **Recommended Activation**: Sigmoid
* **Reasoning**: Predicts a probability value between $0$ and $1$.


* **Regression (Unconstrained target: $y$ can be positive or negative)**
* **Recommended Activation**: Linear
* **Reasoning**: Allows network outputs to span all real numbers from negative to positive infinity.


* **Regression (Non-negative target: $y \ge 0$, e.g., house prices)**
* **Recommended Activation**: ReLU
* **Reasoning**: Ensures model outputs remain non-negative (zero or positive).



### Hidden Layers: ReLU vs. Sigmoid

* **ReLU Advantages**
* Faster to compute computationally (requires only `max(0, z)` without exponential operations).
* Only goes flat on one side (left half), whereas sigmoid flattens on both sides, which can severely slow down gradient descent learning.


* **Best Practice**
* Use **ReLU** as the default choice for all hidden layers in modern deep learning applications.



### Notes

* While other activations like LeakyReLU, tanh, or swish exist and can occasionally offer minor performance boosts, ReLU and sigmoid cover the vast majority of practical use cases.
* The next video will explore why non-linear activation functions are mathematically indispensable to neural networks.


## Video 2.5: Why Neural Networks Need Activation Functions

### Key Concepts

* **Linear Collapse**: The mathematical principle where stacking multiple layers using only linear activation functions collapses the entire multi-layer network into a single equivalent linear or logistic regression model.
* **Need for Non-Linearity**: Non-linear activation functions (like ReLU or sigmoid) are essential for allowing neural networks to learn complex, non-linear relationships and features beyond simple straight lines.

### Topics Covered

* Demonstration of why using linear activation functions everywhere renders a deep neural network mathematically equivalent to standard linear regression.
* Explanation of how a network with linear hidden layers and a sigmoid output layer collapses into standard logistic regression.
* The rule of thumb for hidden layer design (avoid linear activations in hidden layers; use ReLU instead).
* Preview of multi-class classification (predicting more than two categories) in the upcoming video.

### Mathematical Collapse of Linear Networks

* **Single/Multi-Layer Linear Network**
* If $g(z) = z$ for all hidden and output units, a network with sequential linear operations (e.g., $a_2 = w_2(w_1 x + b_1) + b_2$) simplifies algebraically to a single linear combination: $w x + b$.
* **Result**: The network loses all multi-layer depth advantages and behaves exactly like basic linear regression.


* **Linear Hidden Layers + Sigmoid Output**
* If hidden layers use linear activations but the final output layer uses a sigmoid function, the entire model collapses into standard **logistic regression**.
* **Result**: The network cannot learn complex hierarchical features.



### Notes

* Non-linear activation functions (such as ReLU) provide the crucial twist needed to unlock the expressive power of deep neural networks.
* The next video will introduce multi-class classification, extending classification beyond binary outcomes (0 or 1) to multiple categories.
