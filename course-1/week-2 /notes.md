# Week 2: Regression with Multiple Input Variables

## Video 2.1: Multiple Features

### Key Concepts

* **Multiple Linear Regression**: An extension of linear regression that incorporates $n$ distinct input features ($x_1, x_2, \dots, x_n$) to predict a target variable $y$.
* **Feature Vector ($\vec{x}$)**: A list or 1D array containing all input feature values for a specific training example.
* **Parameter Vector ($\vec{w}$)**: A list or 1D array holding the weight parameters corresponding to each input feature.
* **Dot Product ($\vec{w} \cdot \vec{x}$)**: A linear algebra operation that computes the sum of element-wise products across two vectors: $\sum_{j=1}^{n} w_j x_j$.

### Topics Covered

* Expanding univariate linear regression to handle multiple input features using a housing price prediction example
* Introduction of vector notation for features ($\vec{x}$) and weights ($\vec{w}$)
* Interpretation of parameter values in a multi-feature regression model
* Expressing the multiple linear regression model compactly using vector dot products

### Standard Notation Summary

* $n$: Total number of input features
* $m$: Total number of training examples
* $x_j$: The $j$-th feature variable
* $\vec{x}^{(i)}$: The feature vector (list of all features) for the $i$-th training example
* $x_j^{(i)}$: The value of feature $j$ in the $i$-th training example
* $\vec{w}$: Vector of weight parameters $[w_1, w_2, \dots, w_n]$
* $b$: Scalar bias parameter

### Model Equations

* **Expanded Form**: $f_{\vec{w},b}(\vec{x}) = w_1 x_1 + w_2 x_2 + \dots + w_n x_n + b$
* **Vectorized Form**: $f_{\vec{w},b}(\vec{x}) = \vec{w} \cdot \vec{x} + b$

### Notes

* "Multiple linear regression" refers to using multiple input features to predict a single continuous target, distinct from "multivariate regression" which predicts multiple target variables simultaneously.
* Using vector notation simplifies complex mathematical formulas and enables cleaner, more efficient code implementations via linear algebra.
* The next video will introduce vectorization, a computing technique used to implement vector operations efficiently in code.

## Video 2.2: Vectorization

### Key Concepts

* **Vectorization**: The technique of executing operations across entire vectors simultaneously rather than sequentially iterating over individual elements.
* **NumPy (`np`)**: The standard Python numerical linear algebra library used in data science and machine learning for vectorized matrix and vector computations.
* **Parallel Hardware**: Hardware processing capabilities (CPUs and GPUs) that allow computers to execute multiple mathematical operations concurrently.
* **Dot Product Function (`np.dot`)**: A vectorized NumPy function that computes the inner dot product of two vectors in parallel.

### Topics Covered

* Comparison of model implementations: manual expansion, non-vectorized `for` loops, and vectorized code
* Indexing differences between mathematical notation (1-indexed) and Python/NumPy arrays (0-indexed)
* Efficiency benefits of vectorization (shorter code, dramatically faster execution via parallel hardware execution)

### Implementation Approaches Compared ($n = 3$)

* **Manual Expansion (Non-Vectorized)**
* **Code**: `f = w[0]*x[0] + w[1]*x[1] + w[2]*x[2] + b`
* **Drawbacks**: Extremely tedious to write, prone to errors, doesn't scale as feature count $n$ grows.


* **For Loop Iteration (Non-Vectorized)**
* **Code**:
```python
f = 0
for j in range(n):
    f = f + w[j] * x[j]
f = f + b

```


* **Drawbacks**: Executes sequentially step-by-step; fails to utilize modern computer hardware optimization.


* **Vectorized Form (NumPy)**
* **Code**: `f = np.dot(w, x) + b`
* **Advantages**: Single line of code, highly readable, scales efficiently to large datasets by executing operations in parallel across CPU/GPU cores.



### Notes

* Python array indexing begins at `0` (accessing `w[0]` through `w[n-1]`), whereas standard mathematical notation typically indexes from $1$ through $n$.
* Behind the scenes, libraries like NumPy map operations directly to specialized parallel computing hardware, outperforming standard Python `for` loops.
* Vectorized operations are foundational for scaling machine learning algorithms to thousands or millions of features efficiently.

# Video 2.3: How Vectorization Works

### Key Concepts

* **Parallel Computing / Hardware Acceleration**: The ability of modern computer processors (CPUs and GPUs) to execute multiple mathematical operations concurrently in a single clock cycle.
* **SIMD (Single Instruction, Multiple Data)**: The underlying hardware mechanism that allows a vectorized command to process multiple data points simultaneously instead of executing them sequentially.
* **Broadcasting & Element-wise Vector Operations**: Performing mathematical calculations (like multiplication or subtraction) directly across entire arrays in one unified step.

### Topics Covered

* Sequential execution vs. parallel hardware execution
* Detailed visual breakdown of non-vectorized `for` loops vs. vectorized NumPy computations
* Applying vectorization to simultaneous parameter updates in gradient descent ($w = w - \alpha \cdot d$)
* Scalability impact on execution time (reducing compute time from hours to minutes)

### Execution Model Comparison

* **Sequential Execution (Non-Vectorized `for` loop)**
* **Time Step $t_0$**: Computes $w_0 \cdot x_0$
* **Time Step $t_1$**: Computes $w_1 \cdot x_1$
* **Time Step $t_n$**: Computes $w_n \cdot x_n$
* **Result**: Takes $n$ distinct, sequential operational steps.


* **Parallel Execution (Vectorized NumPy Operations)**
* **Single Time Step**: Computes $[w_0 x_0, w_1 x_1, \dots, w_n x_n]$ simultaneously using dedicated hardware lanes, followed by an optimized parallel sum reduction.
* **Result**: Completes in fraction of the time, scaling efficiently to thousands or millions of parameters.



### Gradient Descent Vectorized Update Example

Instead of updating parameters one by one in a loop:

```python
# Non-vectorized update loop
for j in range(16):
    w[j] = w[j] - 0.1 * d[j]

```

Vectorization updates the entire parameter array in a single operation:

```python
# Vectorized update
w = w - 0.1 * d

```

### Notes

* While speed benefits may be modest for small feature sets ($n=16$), vectorization is critical when dealing with large datasets or models with thousands of features.
* Vectorized code drastically improves readability, reduces human coding error, and maps directly to optimized numerical algebra libraries (like NumPy).
* The next video will integrate vectorization directly into gradient descent for multiple linear regression.

# Video 2.4: Gradient Descent for Multiple Linear Regression

### Key Concepts

* **Vectorized Gradient Descent**: Updating all $n$ weight parameters simultaneously using vector mathematical expressions rather than individual element-by-element loops.
* **Partial Derivatives for Multiple Features**: The derivative of the cost function $J(\vec{w}, b)$ with respect to feature weight $w_j$ incorporates the corresponding input feature value $x_j^{(i)}$ for each training example.
* **Normal Equation**: An alternative, non-iterative mathematical method using linear algebra to directly solve for optimal parameters $\vec{w}$ and $b$ in a single step without running gradient descent.

### Topics Covered

* Formulating multiple linear regression using vectorized notation: $f_{\vec{w},b}(\vec{x}) = \vec{w} \cdot \vec{x} + b$
* Gradient descent update rules for each parameter $w_1, w_2, \dots, w_n$ and bias $b$
* Overview, pros, and cons of the Normal Equation compared to iterative Gradient Descent

### Gradient Descent Algorithm Equations

For parameters $j = 1, \dots, n$ and scalar bias $b$, repeatedly update until convergence:

* **Update for Weights ($w_j$)**:

$$w_j = w_j - \alpha \frac{1}{m} \sum_{i=1}^{m} \left( f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)} \right) x_j^{(i)}$$


* **Update for Bias ($b$)**:

$$b = b - \alpha \frac{1}{m} \sum_{i=1}^{m} \left( f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)} \right)$$



*(Note: Parameters $w_1, w_2, \dots, w_n$ and $b$ are updated simultaneously on every iteration.)*

### Gradient Descent vs. Normal Equation

* **Gradient Descent**
* **Approach**: Iterative algorithm that optimizes parameters step-by-step.
* **Generality**: Applies broadly to Linear Regression, Logistic Regression, Neural Networks, and other ML algorithms.
* **Scalability**: Scales effectively to large datasets and high feature counts ($n$).
* **Usage**: The standard choice for custom ML implementations and large-scale problems.


* **Normal Equation**
* **Approach**: Direct analytical solution calculated in a single mathematical step.
* **Generality**: Applies almost exclusively to Linear Regression.
* **Scalability**: Becomes computationally slow and memory-heavy when $n$ is very large.
* **Usage**: Used internally by certain machine learning libraries for linear models.



### Notes

* While the Normal Equation avoids choosing a learning rate $\alpha$ or running iterations, its computational complexity makes it inefficient for datasets with large numbers of features ($n$).
* Vectorized gradient descent remains the foundation for training modern large-scale machine learning models.
* The next video will cover practical feature engineering tricks, such as feature scaling, to speed up gradient descent convergence.
