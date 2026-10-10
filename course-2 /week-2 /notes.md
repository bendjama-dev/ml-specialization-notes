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
