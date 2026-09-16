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
