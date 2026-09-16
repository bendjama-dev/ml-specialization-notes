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


