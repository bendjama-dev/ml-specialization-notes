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

# Video 2.5: Feature Scaling

### Key Concepts

* **Feature Scaling**: Transforming numerical features so they share comparable ranges, preventing disparity in weight updates.
* **Contour Plot Distortion**: When features operate on drastically different scales, the cost function $J(\vec{w},b)$ forms tall, elongated elliptical contours.
* **Gradient Descent Efficiency**: Scaling reshapes the cost function contours into spherical/circular forms, allowing gradient descent to take a direct path to the global minimum rather than oscillating.

### Topics Covered

* Relationship between feature magnitude and weight magnitude ($w_j$)
* Visualizing unscaled features vs. scaled features on scatter plots and cost function contour maps
* Impact of feature scale disparity on gradient descent convergence speed

### Feature Magnitude vs. Weight Magnitude

* **Large Feature Range (e.g., House Size: $300$ to $2,000$ sq ft)**
* A small change in $w_1$ produces a massive change in predictions and cost.
* Optimal model weights ($w_1$) tend to be relatively small (e.g., $0.1$).


* **Small Feature Range (e.g., Bedrooms: $0$ to $5$)**
* A large change in $w_2$ is needed to impact predictions and cost.
* Optimal model weights ($w_2$) tend to be relatively large (e.g., $50$).



### Why Feature Scaling Speeds Up Gradient Descent

* **Unscaled Features**
* **Contour Shape**: Extremely tall, narrow ovals / ellipses.
* **Gradient Trajectory**: Gradient descent bounces back and forth repeatedly across steep gradients, making slow progress toward the minimum.


* **Scaled Features**
* **Contour Shape**: Concentric circles.
* **Gradient Trajectory**: Gradient descent moves directly toward the global minimum, requiring fewer iterations to converge.



### Notes

* Rescaling features to comparable ranges (e.g., $0$ to $1$) reduces computational overhead and training time.
* Feature scaling does not alter the underlying relationship in the data; it simply re-parameterizes the optimization space for the solver.
* The next video will cover specific mathematical methods to perform feature scaling, such as Mean Normalization and Z-score Normalization.

# Video 2.6: Implementing Feature Scaling

### Key Concepts

* **Division by Maximum**: Simple feature scaling by dividing every data point by the maximum value in that feature's dataset.
* **Mean Normalization**: Re-centering features around a mean ($\mu$) of zero, producing both positive and negative values.
* **Z-Score Normalization**: Standardizing features based on mean ($\mu$) and standard deviation ($\sigma$).
* **Standard Deviation ($\sigma$)**: A statistical measure of how spread out numbers are relative to their mean.

### Topics Covered

* Mathematical formulas for three feature scaling techniques: Division by Maximum, Mean Normalization, and Z-score Normalization.
* Scaling targets and rules of thumb for practical machine learning implementations.
* Identifying when a feature needs scaling versus when it can be left as-is.

### Scaling Methods & Formulas

* **Division by Maximum**
* **Formula**: $x_j = \frac{x_j}{\max(x_j)}$
* **Effect**: Scales feature values into a non-negative range, typically between $0$ and $1$.


* **Mean Normalization**
* **Formula**: $x_j = \frac{x_j - \mu_j}{\max(x_j) - \min(x_j)}$
* **Effect**: Centers the feature around $0$, typically creating values between $-1$ and $+1$.


* **Z-Score Normalization**
* **Formula**: $x_j = \frac{x_j - \mu_j}{\sigma_j}$
* **Effect**: Transforms feature values so the mean becomes $0$ and standard deviation becomes $1$, typically yielding values around $-3$ to $+3$.



### Guidelines for Feature Scaling

* **Target Range**: Aim to scale features so they roughly lie within $[-1, +1]$.
* **Acceptable Ranges (No scaling strictly required)**:
* $[-3, +3]$
* $[-0.3, +0.3]$
* $[0, 3]$
* $[-2, +0.5]$


* **Requires Feature Scaling**:
* Large ranges like $[-100, +100]$
* Extremely small ranges like $[-0.001, +0.001]$
* Values shifted away from zero, such as body temperatures $[98.6, 105]$ °F



### Notes

* Standard rules of thumb for feature scaling are flexible; exact boundaries of $[-1, +1]$ are not strictly required.
* Performing feature scaling rarely harms model performance—when in doubt, apply it.
* The next video will discuss how to verify whether gradient descent is converging properly to the global minimum.

# Video 2.7: Checking Gradient Descent for Convergence

### Key Concepts

* **Learning Curve**: A plot showing the cost function $J(\vec{w},b)$ on the vertical axis against the number of gradient descent iterations on the horizontal axis.
* **Convergence**: The state where gradient descent has successfully minimized the cost function $J(\vec{w},b)$, causing the learning curve to flatten out.
* **Automatic Convergence Test**: A programmatic test that declares convergence when the reduction in cost $J$ per iteration falls below a small predefined threshold ($\epsilon$).

### Topics Covered

* Visualizing convergence using a learning curve plot
* Identifying improper gradient descent behavior or bugs in the implementation
* Comparing visual learning curves against automatic convergence tests

### Identifying Convergence & Bugs

* **Proper Gradient Descent Execution**
* Cost $J(\vec{w},b)$ should decrease after **every single iteration**.
* The curve eventually flattens out, indicating the algorithm has converged near the global minimum.
* The number of required iterations varies drastically by problem (ranging from $30$ to $100,000+$ iterations).


* **Signs of Error or Bad Parameters**
* If cost $J(\vec{w},b)$ **increases** after an iteration, the learning rate $\alpha$ is usually set too large, or there is a bug in the code implementation.



### Convergence Detection Methods

* **Visual Inspection (Learning Curve)**
* **Method**: Plot $J(\vec{w},b)$ versus iteration count.
* **Pros**: Highly reliable, provides immediate visual feedback if the learning rate is too high or if the model is still learning.
* **Cons**: Requires manual review of plots.


* **Automatic Convergence Test**
* **Method**: Declare convergence when $\Delta J < \epsilon$ (where $\epsilon = 10^{-3} = 0.001$).
* **Pros**: Can be automated programmatically to halt training without user intervention.
* **Cons**: Choosing a suitable threshold $\epsilon$ is difficult in practice.



### Notes

* Visualizing the learning curve is generally preferred over automatic convergence testing because it gives early warning signs if gradient descent is misbehaving.
* The next video will discuss how to systematically select an appropriate learning rate $\alpha$.

# Video 2.8: Setting the Learning Rate

### Key Concepts

* **Learning Rate ($\alpha$)**: A hyperparameter that controls the step size taken towards the global minimum during each iteration of gradient descent.
* **Overshooting**: A condition where a large learning rate causes update steps to jump past the cost function's minimum, causing cost divergence or oscillation.
* **Systematic Search Grid**: Testing learning rates in rough multiplicative increments of $3\times$ (e.g., $0.001 \to 0.003 \to 0.01 \to 0.03 \to 0.1 \dots$) to quickly locate optimal behavior.

### Topics Covered

* Identifying signs of a faulty learning rate vs. code bugs via learning curves
* Debugging gradient descent implementations using an artificially small $\alpha$
* Choosing a strategy to systematically test and select the optimal learning rate

### Impact of Learning Rate ($\alpha$) Choices

* **Learning Rate Too Large**
* **Symptoms**: Cost function $J(\vec{w},b)$ oscillates up and down, or monotonically increases across iterations.
* **Cause**: Update steps jump over the local/global minimum.
* **Fix**: Decrease the value of $\alpha$.


* **Learning Rate Too Small**
* **Symptoms**: Cost function decreases consistently, but convergence takes an excessively high number of iterations.
* **Cause**: Update steps towards the gradient minimum are unnecessarily tiny.



### Debugging & Tuning Strategies

* **Debugging Tip**
* Set $\alpha$ to a very small number (e.g., $10^{-6}$).
* If $J(\vec{w},b)$ still increases on *any* iteration, there is a bug in the code (such as adding the gradient derivative instead of subtracting it: $\vec{w} = \vec{w} + \alpha \frac{\partial J}{\partial \vec{w}}$).
* If $J(\vec{w},b)$ decreases on every iteration with a tiny $\alpha$, the algorithm implementation is correct.


* **Selection Strategy**
* Try a grid of values spaced roughly by factors of three:

$$0.001 \longrightarrow 0.003 \longrightarrow 0.01 \longrightarrow 0.03 \longrightarrow 0.1 \longrightarrow 0.3 \dots$$


* Run each setting for a few iterations and plot $J(\vec{w},b)$ against iteration count.
* Select the largest value of $\alpha$ that decreases the cost $J(\vec{w},b)$ rapidly and consistently without overshooting.



### Notes

* Choosing a very small $\alpha$ is strictly a **debugging tool** to verify code correctness, not an efficient setting for actual training.
* The upcoming materials move into feature engineering and polynomial regression (fitting curves rather than straight lines).

# Video 2.10: Polynomial Regression

### Key Concepts

* **Polynomial Regression**: A form of regression analysis in which the relationship between the independent variable $x$ and the dependent variable $y$ is modeled as an $n$-th degree polynomial (e.g., using $x^2, x^3, \sqrt{x}$).
* **Non-Linear Transformations**: Transforming features using powers or roots to fit curves and non-linear patterns while maintaining a standard linear regression framework.

### Topics Covered

* Fitting non-linear functions using polynomial feature transformations
* Comparing model shapes (Quadratic vs. Cubic vs. Square Root)
* Critical role of Feature Scaling when using higher-order polynomial terms
* Course progress recap and introduction to Scikit-learn

### Model Comparison & Behavior

* **Quadratic Model ($f_{\vec{w},b}(x) = w_1 x + w_2 x^2 + b$)**
* **Shape**: Parabolic curve.
* **Limitation**: Eventually turns downwards, which is inappropriate for domain metrics like housing prices that should continuously increase with size.


* **Cubic Model ($f_{\vec{w},b}(x) = w_1 x + w_2 x^2 + w_3 x^3 + b$)**
* **Shape**: S-shaped polynomial curve.
* **Advantage**: Allows the model to flatten and turn upward as house size increases, offering a better fit.


* **Square Root Model ($f_{\vec{w},b}(x) = w_1 x + w_2 \sqrt{x} + b$)**
* **Shape**: Sub-linear curve that flattens out as $x$ increases.
* **Advantage**: Continuously increases without ever coming back down, capturing diminishing returns on property size.



### Importance of Feature Scaling in Polynomial Regression

When adding higher-power terms, feature ranges diverge drastically:

* If $x \in [1, 1000]$, then $x^2 \in [1, 10^6]$ and $x^3 \in [1, 10^9]$.
* Because features take on vastly different numeric ranges, applying **Feature Scaling** (e.g., Z-Score Normalization) becomes mandatory for gradient descent to converge effectively.

### Practical Implementation

* **Scikit-learn**: Industry-standard Python machine learning toolkit that allows rapid model building with concise code.
* **Manual vs. Library Code**: Building algorithms from scratch builds deep intuition, while libraries like Scikit-learn streamline production deployment.

### Course Roadmap

* **This Week's Labs**: Practice implementing linear regression manually and with Scikit-learn.
* **Next Week**: Transitioning from regression (predicting continuous values) to **classification** (predicting discrete categories).
