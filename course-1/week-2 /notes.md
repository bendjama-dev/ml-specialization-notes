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
