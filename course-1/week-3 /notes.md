# Week 3: Classification 
## **Video 3.1: Classification and Logistic Regression Motivation**

---

**Key Concepts**

* **Classification:** A learning task where the output variable $y$ takes on discrete values (categories) rather than any value in a continuous range.
* **Binary Classification:** A classification problem with only two possible output values, usually designated as $0$ and $1$.
* **Negative Class ($0$):** Standard convention representing the absence, "No", or "False" state of a property (e.g., non-spam, benign tumor).
* **Positive Class ($1$):** Standard convention representing the presence, "Yes", or "True" state of a property (e.g., spam, malignant tumor).
* **Decision Boundary:** A dividing line or threshold used to separate predicted classes based on model outputs.

**Topics Covered**

* Distinguishing between continuous output tasks (linear regression) and discrete output tasks (classification).
* Practical examples of binary classification: email spam filtering, financial fraud detection, and tumor classification.
* Standard conventions for labeling positive and negative target classes using $y \in \{0, 1\}$.
* Demonstrating why fitting a linear regression line fails for classification tasks when data includes far-off outliers.
* Introducing the need for **logistic regression** to constrain predictions strictly between $0$ and $1$.

**Standard Notation Summary**

* **$y$**: Output target variable ($y = 0$ or $y = 1$)
* **Class $0$**: Negative class (False / No)
* **Class $1$**: Positive class (True / Yes)
* **Threshold**: Cut-off value (commonly $0.5$) used to convert continuous values into discrete predictions

**Model Equations**

* **Linear Regression Thresholding (Attempted):**
* Predict $y = 1$ if $f(\vec{x}) \ge 0.5$
* Predict $y = 0$ if $f(\vec{x}) < 0.5$



**Notes**

* Despite having "regression" in its name for historical reasons, **logistic regression** is a classification algorithm, not a regression algorithm.
* Adding a single distant data point shifts the best-fit linear regression line, which shifts the decision boundary and leads to inaccurate predictions.
* The terms "positive" and "negative" do not imply good vs. bad; they simply indicate the presence or absence of the feature being tested.

## **Video 3.2: Logistic Regression Model**

---

**Key Concepts**

* **Logistic Regression:** A widely used classification algorithm that fits an S-shaped curve to data, constraining model predictions strictly between $0$ and $1$.
* **Sigmoid Function:** Also called the logistic function, $g(z)$ maps any real-valued number $z$ into an output range between $0$ and $1$.
* **Probability Output:** The model prediction $f(\vec{x})$ represents the probability that the output variable $y$ belongs to the positive class ($1$), given input features $\vec{x}$.

**Topics Covered**

* Transitioning from linear regression to an S-shaped curve for classification problems.
* Derivation and behavior of the Sigmoid function $g(z) = \frac{1}{1 + e^{-z}}$.
* Combining the linear combination $z = \vec{w} \cdot \vec{x} + b$ with the Sigmoid function to form the complete logistic regression model.
* Interpreting predictions as conditional probabilities $P(y=1\vert{}\vec{x})$ and calculating complementary probabilities $P(y=0\vert{}\vec{x})$.
* Practical industry applications, such as ad targeting algorithms in large tech companies.

**Standard Notation Summary**

* **$z$**: Intermediate variable representing linear regression: $\vec{w} \cdot \vec{x} + b$
* **$g(z)$**: Sigmoid function applied to $z$
* **$e$**: Euler's number (mathematical constant $\approx 2.718$)
* **$P(y=1 \vert{} \vec{x}; \vec{w}, b)$**: Probability that $y=1$ given feature vector $\vec{x}$ and model parameters $\vec{w}, b$

**Model Equations**

* **Sigmoid Function:** $g(z) = \frac{1}{1 + e^{-z}}$
* **Linear Parameter Output:** $z = \vec{w} \cdot \vec{x} + b$
* **Logistic Regression Model:** $f_{\vec{w},b}(\vec{x}) = g(\vec{w} \cdot \vec{x} + b) = \frac{1}{1 + e^{-(\vec{w} \cdot \vec{x} + b)}}$
* **Probability Complement Rule:** $P(y=0 \vert{} \vec{x}) = 1 - P(y=1 \vert{} \vec{x})$

**Notes**

* **Asymmetric Limits:** When $z$ is large and positive, $e^{-z} \to 0$, so $g(z) \to 1$. When $z$ is large and negative, $e^{-z} \to \infty$, so $g(z) \to 0$. At $z=0$, $g(0) = 0.5$.
* **Probability vs. Prediction:** Although the model outputs continuous probabilities (e.g., $0.7$ or $70\%$), the true target label $y$ is strictly binary ($0$ or $1$).
* **Semicolon Notation:** In $P(y=1 \vert{} x; w, b)$, the semicolon separates the input variable $x$ from the model parameters $w$ and $b$.

## **Video 3.3: Decision Boundary**

---

**Key Concepts**

* **Decision Boundary:** A line, curve, or surface defined by the condition $z = 0$ (or $\vec{w} \cdot \vec{x} + b = 0$) that separates the regions where a logistic regression model predicts $y=1$ versus $y=0$ [cite: ].
* **Thresholding Predictions:** A standard choice is to predict $\hat{y} = 1$ when the model output $f(\vec{x}) \ge 0.5$ and $\hat{y} = 0$ when $f(\vec{x}) < 0.5$ [cite: ].
* **Linear vs. Non-linear Boundaries:** Standard features produce linear decision boundaries (straight lines), while higher-order polynomial features allow the model to learn complex, non-linear shapes like circles, ellipses, or intricate contours [cite: ].

**Topics Covered**

* Recapping the two-step computation of logistic regression: computing $z = \vec{w} \cdot \vec{x} + b$ and passing it through the Sigmoid function $g(z)$ [cite: ].
* Mathematical derivation showing that predicting $f(\vec{x}) \ge 0.5$ is equivalent to checking when the linear expression $\vec{w} \cdot \vec{x} + b \ge 0$ [cite: ].
* Visualizing a linear decision boundary using two features ($x_1, x_2$) with specific parameters ($w_1=1, w_2=1, b=-3$) [cite: ].
* Creating non-linear decision boundaries (such as a circular boundary) by incorporating polynomial features like $x_1^2 + x_2^2 = 1$ [cite: ].
* Demonstrating how higher-order polynomial terms enable the model to fit complex, highly non-linear data distributions [cite: ].

**Standard Notation Summary**

* **$f(\vec{x})$**: Logistic regression model output representing the estimated probability $P(y=1\vert{}\vec{x})$ [cite: ].
* **$\hat{y}$**: The discrete binary prediction ($0$ or $1$) [cite: ].
* **$z$**: The intermediate linear or polynomial term ($\vec{w} \cdot \vec{x} + b$) [cite: ].
* **Decision Boundary Condition**: $z = 0 \implies \vec{w} \cdot \vec{x} + b = 0$ [cite: ].

**Model Equations & Rules**

* **Prediction Threshold Rule:**
* If $f(\vec{x}) \ge 0.5 \implies \hat{y} = 1$ (occurs when $z \ge 0$) [cite: ]
* If $f(\vec{x}) < 0.5 \implies \hat{y} = 0$ (occurs when $z < 0$) [cite: ]


* **Linear Decision Boundary Example:** $x_1 + x_2 - 3 = 0 \implies x_1 + x_2 = 3$ [cite: ]
* **Circular Polynomial Decision Boundary Example:** $x_1^2 + x_2^2 - 1 = 0 \implies x_1^2 + x_2^2 = 1$ [cite: ]

**Notes**

* The decision boundary is a property of the model and its parameters, not of the dataset itself [cite: ].
* Without higher-order polynomial features, the decision boundary for logistic regression will always be a straight line (linear) [cite: ].
* In the next steps of the course, focus shifts to defining the cost function for logistic regression and applying gradient descent for model training [cite: ].


## **Video 3.4: Cost Function for Logistic Regression**

---

**Key Concepts**

* **Loss Function ($L$):** Measures how well a model performs on a single training example [cite: ].
* **Cost Function ($J$):** Measures overall performance across the entire dataset by taking the average loss over all training examples [cite: ].
* **Non-Convexity:** A surface with multiple local minima where gradient descent can get stuck [cite: ].
* **Convexity:** A smooth, bowl-shaped surface with a single global minimum, guaranteeing gradient descent convergence [cite: ].

**Topics Covered**

* Explaining why the squared error cost function is unsuitable for logistic regression (it produces a non-convex cost surface with local minima) [cite: ].
* Introducing the loss function $L(f(\vec{x}), y)$ to evaluate single predictions against true binary targets ($y=1$ or $y=0$) [cite: ].
* Visualizing the behavior of the logarithmic loss curve for $y=1$ and $y=0$ [cite: ].
* Demonstrating how the new loss function heavily penalizes confident, incorrect predictions (approaching infinite loss) [cite: ].
* Defining the overall logistic regression cost function as the average loss across all $m$ training examples [cite: ].

**Standard Notation Summary**

* **$m$**: Total number of training examples [cite: ]
* **$n$**: Total number of features [cite: ]
* **$L(f(\vec{x}), y)$**: Loss computed on a single training example [cite: ]
* **$J(\vec{w}, b)$**: Overall cost function parameterized by weights $\vec{w}$ and bias $b$ [cite: ]

**Model Equations**

* **Squared Error Loss (Not recommended for logistic regression):**

$$L(f(\vec{x}), y) = \frac{1}{2}(f(\vec{x}) - y)^2 \quad \text{(Results in non-convex } J(\vec{w},b)\text{)}$$



[cite: ]
* **Logistic Regression Loss Function (Piecewise):**

$$L(f(\vec{x}), y) = \begin{cases} -\log(f(\vec{x})) & \text{if } y = 1 \\ -\log(1 - f(\vec{x})) & \text{if } y = 0 \end{cases}$$



[cite: ]
* **Overall Cost Function:**

$$J(\vec{w}, b) = \frac{1}{m} \sum_{i=1}^{m} L\left(f\left(\vec{x}^{(i)}\right), y^{(i)}\right)$$



[cite: ]

**Notes**

* Using linear regression's squared error cost function with the non-linear Sigmoid output produces a non-convex surface, causing gradient descent to fail [cite: ].
* When $y=1$, as $f(\vec{x}) \to 1$, loss $\to 0$; as $f(\vec{x}) \to 0$, loss $\to \infty$ [cite: ].
* When $y=0$, as $f(\vec{x}) \to 0$, loss $\to 0$; as $f(\vec{x}) \to 1$, loss $\to \infty$ [cite: ].
* This logarithmic loss function restores convexity, ensuring gradient descent reliably finds the global minimum [cite: ].

## **Video 3.5: Simplified Cost Function for Logistic Regression**

---

**Key Concepts**

* **Simplified Loss Function:** A single algebraic expression that unifies the conditional cases of binary loss ($y=1$ and $y=0$) into one equation [cite: ].
* **Maximum Likelihood Estimation (MLE):** A principle from statistics used to formally derive this convex cost function for logistic regression models [cite: ].
* **Logistic Cost Function:** The average loss across all $m$ training examples, universally used to fit parameters in logistic regression [cite: ].

**Topics Covered**

* Combining the two-part piecewise loss function into a single mathematical expression [cite: ].
* Algebraic proof showing how the unified formula evaluates identically for both $y=1$ and $y=0$ [cite: ].
* Deriving the full cost function $J(\vec{w}, b)$ by averaging individual losses across the entire training set [cite: ].
* Explaining the statistical grounding (Maximum Likelihood Estimation) behind the choice of function [cite: ].
* Linking lower cost values to better-fitting decision boundaries in practical implementations [cite: ].

**Standard Notation Summary**

* **$y$**: True target label ($y \in \{0, 1\}$) [cite: ]
* **$f(\vec{x})$**: Model prediction $f_{\vec{w},b}(\vec{x})$ representing probability $P(y=1\vert{}\vec{x})$ [cite: ]
* **$m$**: Total number of training examples [cite: ]
* **$J(\vec{w}, b)$**: Overall cost function for parameters $\vec{w}$ and $b$ [cite: ]

**Model Equations**

* **Simplified Single-Example Loss Function:**

$$L(f(\vec{x}), y) = -y \log(f(\vec{x})) - (1 - y) \log(1 - f(\vec{x}))$$



[cite: ]
* **Equivalence Check when $y = 1$:**

$$L(f(\vec{x}), 1) = -(1)\log(f(\vec{x})) - (1-1)\log(1-f(\vec{x})) = -\log(f(\vec{x}))$$



[cite: ]
* **Equivalence Check when $y = 0$:**

$$L(f(\vec{x}), 0) = -(0)\log(f(\vec{x})) - (1-0)\log(1-f(\vec{x})) = -\log(1-f(\vec{x}))$$



[cite: ]
* **Full Logistic Regression Cost Function:**

$$J(\vec{w}, b) = -\frac{1}{m} \sum_{i=1}^{m} \left[ y^{(i)} \log\left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right)\right) + \left(1 - y^{(i)}\right) \log\left(1 - f_{\vec{w},b}\left(\vec{x}^{(i)}\right)\right) \right]$$



[cite: ]

**Notes**

* Because $y$ can only be $0$ or $1$, the single-line formulation toggles off the inactive logarithmic term automatically [cite: ].
* Factoring out the negative sign simplifies coding implementation when computing gradient descent [cite: ].
* The convexity of this specific cost function guarantees that optimization algorithms will converge to the global minimum rather than getting trapped in local minima [cite: ].


## **Video 3.6: Gradient Descent for Logistic Regression**

---

**Key Concepts**

* **Parameter Optimization:** Applying the gradient descent algorithm to iteratively find parameter values $\vec{w}$ and $b$ that minimize the cost function $J(\vec{w}, b)$ [cite: ].
* **Simultaneous Updates:** Computing all parameter updates for weights $w_1, w_2, \dots, w_n$ and bias $b$ concurrently at each iteration step before overwriting existing values [cite: ].
* **Optimization Enhancements:** Applying feature scaling to normalize input features and monitoring learning curves to ensure proper convergence work identically in logistic regression as in linear regression [cite: ].

**Topics Covered**

* Formulating gradient descent updates specifically for logistic regression parameters [cite: ].
* Presenting partial derivative expressions for the cost function $J(\vec{w}, b)$ with respect to individual weights $w_j$ and bias $b$ [cite: ].
* Clarifying why the gradient update formula appears identical to linear regression despite computing completely different predictions [cite: ].
* Highlighting the role of vectorization and feature scaling in accelerating gradient descent calculations [cite: ].
* Introducing `scikit-learn` as an industry-standard Python library used by ML practitioners to train logistic regression models [cite: ].

**Standard Notation Summary**

* **$\alpha$**: Learning rate parameter controlling update step size [cite: ]
* **$w_j$**: Weight parameter corresponding to feature $j$ [cite: ]
* **$b$**: Bias scalar parameter [cite: ]
* **$f_{\vec{w},b}(\vec{x})$**: Sigmoid prediction function $g(\vec{w} \cdot \vec{x} + b)$ [cite: ]
* **$x_j^{(i)}$**: Value of feature $j$ for training example $i$ [cite: ]

**Model Equations**

* **Parameter Update Rules:**
* $w_j := w_j - \alpha \frac{\partial J(\vec{w},b)}{\partial w_j}$ [cite: ]
* $b := b - \alpha \frac{\partial J(\vec{w},b)}{\partial b}$ [cite: ]


* **Gradient Formulas:**
* $\frac{\partial J(\vec{w},b)}{\partial w_j} = \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right) - y^{(i)}\right) x_j^{(i)}$ [cite: ]
* $\frac{\partial J(\vec{w},b)}{\partial b} = \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right) - y^{(i)}\right)$ [cite: ]


* **Logistic Model Definition:**
* $f_{\vec{w},b}(\vec{x}) = \frac{1}{1 + e^{-(\vec{w} \cdot \vec{x} + b)}}$ [cite: ]



**Notes**

* **Formulation Distinction:** Although derivative formulas look visually identical to linear regression, logistic regression uses $f_{\vec{w},b}(\vec{x}) = \frac{1}{1 + e^{-z}}$ instead of $f_{\vec{w},b}(\vec{x}) = \vec{w} \cdot \vec{x} + b$, making them distinct algorithms [cite: ].
* **Feature Scaling:** Scaling features to similar numerical ranges (e.g., between $-1$ and $+1$) speeds up gradient descent convergence for logistic regression [cite: ].
* **Industry Implementation:** While building gradient descent from scratch builds foundational knowledge, professional software production typically relies on libraries like `scikit-learn` [cite: ].  

## **Video 3.7: The Problem of Overfitting**

---

**Key Concepts**

* **Underfitting (High Bias):** Occurs when a model is too simple to capture the underlying structure of the training data, performing poorly even on the training set [cite: ].
* **Overfitting (High Variance):** Occurs when a model is overly complex, fitting the training set almost perfectly (including noise) but failing to generalize to new data [cite: ].
* **Generalization:** The ability of a machine learning model to make accurate predictions on brand new, unseen data [cite: ].
* **"Just Right" Model:** A balanced model that captures the true underlying pattern, avoiding both high bias and high variance to maximize generalization [cite: ].

**Topics Covered**

* Demonstrating underfitting, "just right", and overfitting using housing price prediction (linear regression) [cite: ].
* Defining high bias as strong preconceptions about data shape and high variance as extreme sensitivity to small dataset changes [cite: ].
* Extending overfitting and underfitting concepts to binary classification tasks (logistic regression) [cite: ].
* Examining how increasing polynomial degree ($x$ vs. $x^2$ vs. $x^4$) affects decision boundary complexity [cite: ].
* Previewing **regularization** as a key technique to reduce overfitting [cite: ].

**Standard Notation Summary**

* **High Bias:** Equivalent term for underfitting [cite: ].
* **High Variance:** Equivalent term for overfitting [cite: ].
* **$y$**: Target variable [cite: ]
* **$\vec{x}$**: Feature vector (e.g., house size, tumor size, patient age) [cite: ]

**Model Equations**

* **Underfit (Linear Fit):** $f(\vec{x}) = w_1 x + b$ [cite: ]
* **"Just Right" (Quadratic Fit):** $f(\vec{x}) = w_1 x + w_2 x^2 + b$ [cite: ]
* **Overfit (4th-Order Polynomial Fit):** $f(\vec{x}) = w_1 x + w_2 x^2 + w_3 x^3 + w_4 x^4 + b$ [cite: ]

**Notes**

* **Two Meanings of "Bias":** In ML, technical bias refers to model underfitting, whereas social bias refers to unfair predictions regarding demographic traits like ethnicity or gender [cite: ].
* **Zero Cost Warning:** An overfit model can achieve zero training error ($J(\vec{w},b) = 0$), but its erratic predictions make it ineffective for practical use [cite: ].
* Overfitting occurs in both regression tasks and classification tasks with complex decision boundaries [cite: ].

## **Video 3.8: Addressing Overfitting**

---

**Key Concepts**

* **Feature Selection:** The process of choosing a smaller subset of the most relevant features to use in a model, reducing overfitting caused by excessive features [cite: ].
* **Regularization:** A technique that reduces overfitting by encouraging the learning algorithm to shrink parameter values ($w_j$) without eliminating features outright [cite: ].
* **Parameter Shrinkage:** Reducing the size of weights ($w_1, \dots, w_n$), which prevents features from having an overly large impact and results in smoother, less "wiggly" fitting curves [cite: ].

**Topics Covered**

* Overview of the three primary strategies for resolving overfitting (high variance) [cite: ].
* Collecting additional training data to force complex models toward smoother predictions [cite: ].
* Reducing the number of input features manually or through feature selection algorithms [cite: ].
* Introducing regularization as a gentler alternative to feature elimination [cite: ].
* Standard conventions regarding regularizing weight parameters ($w_j$) versus the bias parameter ($b$) [cite: ].

**Standard Notation Summary**

* **$w_j$**: Weight parameter corresponding to feature $j$ (primary target for regularization) [cite: ].
* **$b$**: Bias scalar parameter (conventionally left unregularized) [cite: ].
* **$m$**: Number of training examples in the dataset [cite: ].
* **$n$**: Total number of features [cite: ].

**Model Equations**

* **Feature Elimination Condition:**

$$w_j = 0 \quad \text{(Equivalent to removing feature } x_j \text{ completely)}$$



[cite: ]
* **Regularization Objective (Conceptual):**

$$\text{Minimize } J(\vec{w},b) \quad \text{subject to smaller values for } \vert{}w_1\vert{}, \vert{}w_2\vert{}, \dots, \vert{}w_n\vert{}$$



[cite: ]

**Notes**

* **More Data First:** Collecting more training data is the single most effective tool against overfitting, but it is not always feasible when data collection is limited [cite: ].
* **Trade-off of Feature Selection:** Discarding features reduces overfitting but throws away potentially relevant information that could improve model accuracy [cite: ].
* **Bias Parameter Convention:** In practice, regularization is usually applied only to the weights $w_1, \dots, w_n$; whether or not you regularize the bias $b$ makes very little practical difference [cite: ].
* **Ubiquity:** Regularization is a fundamental technique used extensively across machine learning, particularly in advanced models like neural networks [cite: ].


## **Video 3.9: Regularized Cost Function**

---

**Key Concepts**

* **Regularization Parameter ($\lambda$):** A hyperparameter that controls the trade-off between fitting the training data closely and keeping parameter values small to prevent overfitting [cite: ].
* **Regularization Term:** An added penalty component ($\frac{\lambda}{2m} \sum_{j=1}^{n} w_j^2$) that discourages weights $w_j$ from becoming excessively large [cite: ].
* **Model Simplification:** Shrinking weight parameters toward zero simplifies the effective complexity of the model, producing smoother and less "wiggly" fitting curves [cite: ].
* **Parameter Trade-off:** Setting $\lambda = 0$ results in no regularization (overfitting), whereas an excessively large $\lambda$ forces all weights near zero (underfitting) [cite: ].

**Topics Covered**

* Developing the intuition of penalizing large parameters (e.g., adding large multipliers to $w_3^2$ and $w_4^2$) to eliminate unwanted high-order polynomial effects [cite: ].
* Generalizing parameter penalties across all weight parameters $w_1, \dots, w_n$ when feature importance is unknown in advance [cite: ].
* Defining the modified cost function $J(\vec{w}, b)$ by combining mean squared error with the regularization penalty [cite: ].
* Explaining why the regularization term is scaled by $\frac{1}{2m}$ alongside the primary cost term [cite: ].
* Demonstrating model behavior under three distinct cases: $\lambda = 0$ (overfit), $\lambda \to \infty$ (underfit), and optimal $\lambda$ (just right) [cite: ].

**Standard Notation Summary**

* **$\lambda$**: Regularization parameter [cite: ]
* **$m$**: Number of training examples [cite: ]
* **$n$**: Number of features [cite: ]
* **$w_j$**: Weight parameter for feature $j$ [cite: ]
* **$b$**: Unregularized bias parameter [cite: ]

**Model Equations**

* **Regularized Linear Regression Cost Function:**

$$J(\vec{w}, b) = \frac{1}{2m} \sum_{i=1}^{m} \left( f_{\vec{w},b}\left(\vec{x}^{(i)}\right) - y^{(i)} \right)^2 + \frac{\lambda}{2m} \sum_{j=1}^{n} w_j^2$$



[cite: ]
* **Regularization Penalty Term:**

$$\text{Penalty} = \frac{\lambda}{2m} \sum_{j=1}^{n} w_j^2$$



[cite: ]
* **Extreme Case ($\lambda \to \infty$):**

$$w_1, w_2, \dots, w_n \approx 0 \implies f(\vec{x}) \approx b \quad \text{(Horizontal line / Underfit)}$$



[cite: ]

**Notes**

* Scaling the regularization term by $\frac{1}{2m}$ keeps the relative impact of $\lambda$ stable even if the training set size $m$ grows [cite: ].
* Standard convention excludes the bias parameter $b$ from regularization, as penalizing $b$ makes very little practical difference to performance [cite: ].
* Selecting an optimal $\lambda$ enables the model to retain high-order features while maintaining a smooth fit that generalizes well to new data [cite: ].

## **Video 3.10: Regularized Linear Regression**

---

**Key Concepts**

* **Weight Shrinkage:** Reorganizing the regularized gradient descent update shows that weight parameters $w_j$ are multiplied by a factor slightly less than $1$ ($1 - \alpha \frac{\lambda}{m}$) on each iteration prior to subtracting the standard gradient step [cite: ].
* **Unregularized Bias Update:** Because the bias parameter $b$ is not regularized, its derivative and gradient update remain identical to standard linear regression [cite: ].
* **Simultaneous Updates:** All weight parameters $w_1, \dots, w_n$ and the bias $b$ must be calculated concurrently before updating parameter values [cite: ].

**Topics Covered**

* Formulating gradient descent update rules for regularized linear regression [cite: ].
* Deriving partial derivatives of the regularized cost function with respect to weights $w_j$ and bias $b$ [cite: ].
* Rearranging the weight update equation to illustrate the intuitive "weight decay" or shrinkage mechanism [cite: ].
* Step-by-step calculus derivation showing how differentiating $\frac{\lambda}{2m} w_j^2$ yields $\frac{\lambda}{m} w_j$ [cite: ].
* Mitigating overfitting when dealing with large feature sets and limited training data [cite: ].

**Standard Notation Summary**

* **$\alpha$**: Learning rate [cite: ]
* **$\lambda$**: Regularization parameter [cite: ]
* **$m$**: Total number of training examples [cite: ]
* **$w_j$**: Weight parameter for feature $j$ [cite: ]
* **$b$**: Unregularized bias parameter [cite: ]

**Model Equations**

* **Regularized Cost Function:**

$$J(\vec{w}, b) = \frac{1}{2m} \sum_{i=1}^{m} \left(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)}\right)^2 + \frac{\lambda}{2m} \sum_{j=1}^{n} w_j^2$$



[cite: ]
* **Partial Derivatives:**

$$\frac{\partial J(\vec{w},b)}{\partial w_j} = \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)}\right) x_j^{(i)} + \frac{\lambda}{m} w_j$$



[cite: ]

$$\frac{\partial J(\vec{w},b)}{\partial b} = \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)}\right)$$



[cite: ]
* **Gradient Descent Weight Update (Rearranged Shrinkage Form):**

$$w_j := w_j \left(1 - \alpha \frac{\lambda}{m}\right) - \alpha \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)}\right) x_j^{(i)}$$



[cite: ]
* **Gradient Descent Bias Update:**

$$b := b - \alpha \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)}\right)$$



[cite: ]

**Notes**

* Because $\alpha, \lambda > 0$ and $m > 0$, the factor $\left(1 - \alpha \frac{\lambda}{m}\right)$ evaluates to a value slightly less than $1$ (e.g., $0.9998$), reducing parameter magnitudes continuously at each iteration [cite: ].
* In calculus, differentiating the penalty term $\frac{\lambda}{2m} w_j^2$ with respect to $w_j$ cancels out the factor of $2$, leaving $\frac{\lambda}{m} w_j$ [cite: ].
* Regularization enables linear regression models to generalize significantly better when trained on datasets with many features and few examples [cite: ].


## **Video 3.11: Regularized Logistic Regression**

---

**Key Concepts**

* **Decision Boundary Smoothing:** Regularization prevents complex decision boundaries caused by high-order polynomial features or high feature counts from overfitting training data [cite: ].
* **Regularized Logistic Loss:** Modifies the binary cross-entropy cost function by adding a weight magnitude penalty term [cite: ].
* **Algorithmic Parity:** Gradient update equations for regularized logistic regression share identical symbolic forms with regularized linear regression, differing only in prediction function $f_{\vec{w},b}(\vec{x})$ [cite: ].

**Topics Covered**

* Mitigating high variance and overfitting in classification tasks using regularization [cite: ].
* Formulating the regularized cost function $J(\vec{w}, b)$ for logistic regression [cite: ].
* Updating gradient descent formulas with the regularization derivative term $\frac{\lambda}{m} w_j$ [cite: ].
* Highlighting the non-regularized status of bias parameter $b$ [cite: ].
* Bridging Course 1 foundational machine learning to Course 2 deep learning and neural networks [cite: ].

**Standard Notation Summary**

* **$\lambda$**: Regularization parameter controlling penalty weight [cite: ]
* **$w_j$**: Weight parameter corresponding to feature $j$ [cite: ]
* **$b$**: Bias scalar parameter (unregularized) [cite: ]
* **$f_{\vec{w},b}(\vec{x})$**: Sigmoid prediction output $g(\vec{w} \cdot \vec{x} + b)$ [cite: ]
* **$m$**: Total number of training examples [cite: ]

**Model Equations**

* **Regularized Logistic Regression Cost Function:**

$$J(\vec{w}, b) = -\frac{1}{m} \sum_{i=1}^{m} \left[ y^{(i)} \log\left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right)\right) + \left(1 - y^{(i)}\right) \log\left(1 - f_{\vec{w},b}\left(\vec{x}^{(i)}\right)\right) \right] + \frac{\lambda}{2m} \sum_{j=1}^{n} w_j^2$$



[cite: ]
* **Partial Derivatives:**

$$\frac{\partial J(\vec{w},b)}{\partial w_j} = \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right) - y^{(i)}\right) x_j^{(i)} + \frac{\lambda}{m} w_j$$



[cite: ]

$$\frac{\partial J(\vec{w},b)}{\partial b} = \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right) - y^{(i)}\right)$$



[cite: ]
* **Gradient Descent Update Rules:**

$$w_j := w_j - \alpha \left( \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right) - y^{(i)}\right) x_j^{(i)} + \frac{\lambda}{m} w_j \right)$$



[cite: ]

$$b := b - \alpha \frac{1}{m} \sum_{i=1}^{m} \left(f_{\vec{w},b}\left(\vec{x}^{(i)}\right) - y^{(i)}\right)$$



[cite: ]
* **Model Prediction Definition:**

$$f_{\vec{w},b}(\vec{x}) = \frac{1}{1 + e^{-(\vec{w} \cdot \vec{x} + b)}}$$



[cite: ]

**Notes**

* Though gradient descent update formulas match regularized linear regression symbolically, $f_{\vec{w},b}(\vec{x})$ incorporates the non-linear sigmoid activation function $g(z)$ [cite: ].
* Bias parameter $b$ remains unregularized, following standard machine learning conventions [cite: ].
* Regularizing weights prevents decision boundaries from curving excessively around single noisy training points, improving out-of-sample generalization [cite: ].
