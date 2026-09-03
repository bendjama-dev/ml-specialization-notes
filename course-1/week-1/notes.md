# Week 1: What is Machine Learning?

## Video 1.1: Welcome to Machine Learning Specialization

### Key Concepts
- Machine Learning: Programs that learn from data
- Supervised Learning: Learning from labeled examples
- Unsupervised Learning: Finding patterns in data

### Topics Covered
- Definition of ML
- Supervised vs Unsupervised Learning
- Why ML is important

### Notes
- ML is used everywhere (email filters, recommendation systems, etc.)
- The course will cover both mathematical theory and practical coding

## Video 1.2: Application of machine learning

### Key Concepts
- Machine Learning: Enabling machines to learn from data to solve problems where explicit programming is impossible
- Artificial General Intelligence (AGI): Building machines as intelligent as humans; a long-term goal that is currently overhyped and decades to centuries away
- Practical Implementation: Combining theoretical knowledge with hands-on coding and optimization techniques

### Topics Covered
- Why Machine Learning is widely used today
- Real-world applications across tech and non-tech industries
- Economic impact and industry demand for ML skills
- Preview of upcoming course topics (ML definitions, terminology, and algorithm types)

### Notes
- Traditional rule-based programming works for simple tasks (like GPS route finding), but complex tasks (web search, speech recognition, autonomous driving, medical diagnosis) require ML
- AI/ML is estimated to create $13 trillion in annual value by 2030, with massive untapped opportunities outside the software industry (e.g., manufacturing, agriculture, healthcare, retail)
- The next video will introduce formal definitions of Machine Learning and cover the main categories of learning algorithms

## Video 1.3: What is machine learning ?

### Key Concepts
- Machine Learning (Arthur Samuel): The field of study that gives computers the ability to learn without being explicitly programmed.
- Supervised Learning: The most widely used type of machine learning in real-world applications, driving the most rapid innovation today.
- Unsupervised Learning: A major category of ML algorithms designed to find structure or patterns in data without explicit labels.
- Overview of major ML categories (Supervised, Unsupervised, Recommender Systems, Reinforcement Learning)

### Topics Covered
- Definition of Machine Learning (Arthur Samuel's informal definition)
- Historical case study: Arthur Samuel's Checkers program (1950s)
- Structure of the Specialization
- The critical importance of practical skills and implementation best practices

### Notes
- Arthur Samuel’s checkers program learned by playing tens of thousands of games against itself; over time, it surpassed human skills, demonstrating that more training data/experience leads to better performance.
- The Specialization breakdown: Courses 1 & 2 cover Supervised Learning, while Course 3 focuses on Unsupervised Learning, Recommender Systems, and Reinforcement Learning.
- Having the ML tools is not enough—knowing how to apply best practices effectively is what separates top engineers from teams that spend months pursuing ineffective approaches.
- The next video will cover formal definitions and applications of Supervised Learning and Unsupervised Learning.

## Video 1.4: Supervised Learning (Regression vs. Classification)

### Key Concepts
- Supervised Learning: Algorithms that learn to map inputs (X) to correct outputs (Y) using labeled training data.
- Regression: A supervised learning task that predicts a continuous numerical value from an infinite range (e.g., house prices).
- Classification: A supervised learning task that predicts discrete categories or classes from a small, finite set (e.g., benign vs. malignant).

### Topics Covered
- Definition and core objective of Supervised Learning
- Regression vs. Classification output types
- Handling single vs. multiple input features (e.g., tumor size and patient age)
- Decision boundaries in classification problems

### Notes
- Supervised learning relies on labeled data, where each input example is paired with its target output or label
- Regression outputs can be any number along a continuum, whereas classification outputs are restricted to specific, discrete categories
- Classification is not limited to binary outcomes (e.g., O or 1); it can handle multi-class predictions, with outputs being numeric or non-numeric categories.
- The next video will explore Unsupervised Learning and how algorithms find patterns in unlabeled data.

## Video 1.5: Supervised Learning Part 2

### Key Concepts
- Classification: A supervised learning task where the algorithm predicts a discrete category or class rather than a continuous number.
- Output Classes / Categories: Interchangeable terms referring to the discrete set of target labels (Y).
- Decision Boundary: A line or hyper-plane fitted by the learning algorithm to separate distinct categories in the feature space.

### Topics Covered
- Definition of Classification in supervised learning
- Binary vs. Multi-class classification (e.g., benign vs. malignant, or identifying specific cancer types)
- Differences between continuous regression targets and discrete classification outputs
- Utilizing multiple input features such as tumor size, patient age, cell thickness, and shape uniformity

### Notes
- Supervised learning relies on explicit input-to-output (X \to Y) mappings trained using datasets with correct target labels ("right answers").
- Regression predicts numbers from an infinitely continuous spectrum, whereas classification predicts values from a small, finite set of discrete categories.
- Classification categories can be non-numeric (e.g., cat vs. dog) or numeric (e.g., 0, 1, 2), but intermediate fractional outputs (e.g., 0.5, 1.7) are not valid class predictions.
- Complex real-world models scale by incorporating dozens or hundreds of input features to fit accurate decision boundaries for medical diagnoses and predictions.
- The next video will cover Unsupervised Learning, the second major paradigm of machine learning algorithms.

## Video 1.6: Unsupervised Learning

### Key Concepts

* Unsupervised Learning: Learning algorithms provided with unlabeled data ($X$ only, without target outputs $Y$) to discover structure, patterns, or interesting groupings independently.
* Clustering: An unsupervised learning method that automatically places unlabeled data points into distinct groups or clusters based on shared features or similarity.
* Market Segmentation: An application of clustering used by organizations to group individuals (or customers) into categories based on shared characteristics or behaviors.

### Topics Covered

* Supervised vs. Unsupervised Learning data structures (labeled $Y$ targets vs. unlabeled raw features)
* Clustering algorithms and how they work without human supervision
* Real-world applications of clustering:
* **Google News**: Grouping hundreds of thousands of daily news articles by topic using shared keywords (e.g., panda, twin, zoo).
* **DNA Microarray Data**: Grouping individuals into genetic types/categories based on gene expression levels.
* **Market Segmentation**: Grouping learners in the DeepLearning.AI community based on their primary motivations (e.g., skill growth, career progression, staying updated).



### Notes

* Unlike supervised learning, there are no predefined "right answers" or manual labels given to the algorithm; it must analyze feature relationships autonomously.
* News topics and patterns change constantly, making manual supervision impractical and necessitating unsupervised techniques.
* The next video will explore additional types of unsupervised learning algorithms beyond clustering.


## Video 1.7: Unsupervised Learning Part 2

### Key Concepts

* Unsupervised Learning Definition: Algorithms supplied only with input features ($X$) without output labels ($Y$), tasked with discovering underlying patterns, structures, or anomalies autonomously.
* Anomaly Detection: An unsupervised learning technique used to identify unusual patterns or outlier events that deviate significantly from expected norms.
* Dimensionality Reduction: A technique used to compress large datasets into lower-dimensional representations while preserving as much critical information as possible.

### Topics Covered

* Formal distinction between supervised ($X \to Y$) and unsupervised ($X$ only) learning
* Overview of key unsupervised learning techniques beyond clustering (Anomaly Detection and Dimensionality Reduction)
* Practice quiz & classification of ML problem types (Spam filtering, News grouping, Market segmentation, Diabetes diagnosis)
* Introduction to upcoming practical tools (Jupyter Notebooks)

### Notes

* **Anomaly Detection** is heavily utilized in financial systems for fraud detection by highlighting unusual transaction behaviors.
* **Dimensionality Reduction** enables high-dimensional data compression with minimal information loss.
* Practice Quiz Categorization:
* **Supervised Learning**: Spam filtering (labeled spam/non-spam) and Diabetes diagnosis (labeled target outcomes, similar to tumor classification).
* **Unsupervised Learning**: Google News story grouping and Market segmentation (discovering natural groupings without prior labels).


* Course Roadmap: Course 3 of the specialization will cover Clustering, Anomaly Detection, and Dimensionality Reduction in detail.
* The next video will introduce **Jupyter Notebooks** and how they are used for hands-on machine learning development.


## Video 1.8: Jupyter Notebooks Preview

### Key Concepts

* Jupyter Notebook: The standard, widely used interactive coding environment in AI, machine learning, and data science for experimenting and prototyping.
* Markdown Cells: Text cells formatted with Markdown used to document explanations, theories, and instructions alongside code.
* Code Cells: Executable Python code blocks that can be run interactively within the browser.

### Topics Covered

* Introduction to Jupyter Notebooks as the primary environment for the course
* Distinction between **Optional Labs** (pre-written code to explore without grading) and **Practice Labs** (hands-on coding assignments starting in Week 2)
* Notebook mechanics: navigating cells, editing text/code, and executing cells using `Shift` + `Enter`

### Notes

* Notebooks used in the course are real industry-standard environments—the same tools utilized by machine learning engineers in major tech companies.
* Optional labs are ungraded and designed for quick execution line-by-line to help build intuition for ML code structures.
* Practical tip: Select a cell, predict its output, press `Shift` + `Enter` to execute, and experiment by modifying code snippets to observe changed behavior.
* Next week introduces formal mathematical formulations of supervised learning algorithms along with hands-on practice labs.

## Video 1.9: Linear Regression Model Part 1

### Key Concepts

* Linear Regression: A supervised learning model that predicts numerical outputs by fitting a straight line to training data.
* Training Set: The dataset used to train a machine learning algorithm to learn patterns and make predictions.
* Feature ($x$): The input variable used to make a prediction (e.g., house size in square feet).
* Target ($y$): The output variable that the algorithm tries to predict (e.g., house price).

### Topics Covered

* Overview of linear regression through a housing price prediction example
* Standard mathematical notation for machine learning datasets
* Differences between continuous numerical outputs (regression) and discrete categorical outputs (classification)

### Standard Notation Summary

* $x$: Input feature / variable
* $y$: Output variable / target variable
* $m$: Total number of training examples (e.g., $m = 47$)
* $(x, y)$: A single training example
* $(x^{(i)}, y^{(i)})$: The $i$-th training example, where the superscript $(i)$ represents the row index in the dataset (not an exponent)

### Notes

* Supervised learning algorithms learn from datasets where the target outputs ("right answers") are already known.
* Linear regression models can output any number along a continuous scale, unlike classification models which are restricted to a finite, discrete set of classes.
* The superscript $(i)$ is used as an index for specific dataset rows (e.g., $x^{(1)} = 2104$ for the first house size) and does not denote mathematical exponentiation.
* The next video will cover how to feed this training set into a learning algorithm to train a model to make predictions.

  # Video 1.10: Linear Regression Model Part 2

### Key Concepts

* **Function / Model ($f$)**: The function generated by the learning algorithm that maps input features ($x$) to predicted outputs ($\hat{y}$). Historically referred to as a hypothesis.
* **Prediction / Estimate ($\hat{y}$)**: The estimated value of $y$ produced by the model (read as "y-hat"), as opposed to the actual true target value $y$.
* **Univariate Linear Regression**: Linear regression with a single input variable or feature ($x$). "Uni" means one, and "variate" means variable.
* **Parameters ($w, b$)**: The values that determine the slope and intercept of the linear function used to make predictions.

### Topics Covered

* The workflow of a supervised learning algorithm ($Training\ Data \to Learning\ Algorithm \to Model\ f$)
* The mathematical representation of linear regression with one variable
* Distinguishing between actual targets ($y$) and predicted estimates ($\hat{y}$)
* Introduction to upcoming concepts: Optional lab for straight-line functions and the fundamental role of the Cost Function

### Standard Formula Representation

* Linear regression function formula:

$$f_{w,b}(x) = wx + b$$



*(Often abbreviated simply as $f(x) = wx + b$)*
* Prediction calculation:

$$\hat{y} = f_{w,b}(x)$$



### Notes

* Supervised learning algorithms take both input features ($x$) and target outputs ($y$) from the training set to produce the model function $f$.
* $y$ represents the true, actual target value from the dataset, whereas $\hat{y}$ represents the model's estimate, which may or may not equal the true value.
* Linear functions (straight lines) serve as a simple foundation before progressing to complex non-linear models (curves/parabolas).
* Constructing a **Cost Function** will be the next critical step to evaluate and adjust the parameters $w$ and $b$ to achieve the best fit for the data.

  # Video 1.11: Cost Function Formula

### Key Concepts

* **Parameters ($w, b$)**: The variables of the model that can be adjusted during training to improve its predictions. $w$ controls the slope, and $b$ controls the y-intercept.
* **Error**: The difference between the model's predicted output ($\hat{y}$) and the actual target value ($y$), computed as $(\hat{y} - y)$.
* **Cost Function ($J(w, b)$)**: A quantitative measure that evaluates how well the model's predictions fit the training dataset overall.
* **Squared Error Cost Function**: The standard cost function used for linear regression that averages the sum of squared errors across all training examples.

### Topics Covered

* How changing parameters $w$ and $b$ affects the straight-line prediction function $f(x)$
* Mathematical construction of the error term for individual training examples
* Formulation of the Mean Squared Error (MSE) cost function divided by $2m$

### Standard Formula Representation

* Model prediction for example $i$:

$$\hat{y}^{(i)} = f_{w,b}(x^{(i)}) = w x^{(i)} + b$$


* Squared Error Cost Function formula:

$$J(w,b) = \frac{1}{2m} \sum_{i=1}^{m} \left( \hat{y}^{(i)} - y^{(i)} \right)^2$$


* Expanded form:

$$J(w,b) = \frac{1}{2m} \sum_{i=1}^{m} \left( f_{w,b}(x^{(i)}) - y^{(i)} \right)^2$$



### Notes

* Selecting $w = 0$ results in a horizontal line where predictions always equal the constant $b$.
* The division by $m$ computes the average squared error across all $m$ training examples so that the cost value remains comparable regardless of dataset size.
* The extra factor of $\frac{1}{2}$ in the denominator is added by convention to simplify mathematical derivatives in subsequent optimization steps.
* The next video will explore visual intuitions behind how different values of $w$ and $b$ yield smaller or larger cost values $J(w, b)$.

# Video 1.12: Cost Function Intuition

### Key Concepts

* **Simplified Model**: A linear regression model where the parameter $b$ is set to $0$ ($f(x) = wx$), forcing the best-fit line to pass through the origin $(0,0)$.
* **Cost Minimization**: The primary objective of training a machine learning model, which is finding the parameter value(s) that yield the smallest possible cost value $J$.
* **Cost Function Geometry**: Plotting $J(w)$ against $w$ creates a U-shaped convex curve (parabola) where the global minimum corresponds to the optimal parameter $w$.

### Topics Covered

* Comparison of prediction function graphs ($f_w(x)$ vs $x$) and cost function graphs ($J(w)$ vs $w$)
* Step-by-step mathematical evaluation of $J(w)$ for different parameter values ($w = 1$, $w = 0.5$, $w = 0$, $w = -0.5$)
* Visual mapping from lines on the dataset plot to individual coordinate points on the cost function curve

### Step-by-Step Cost Calculations ($m = 3$ dataset: $(1,1), (2,2), (3,3)$)

* **When $w = 1$**:
* Predictions match targets exactly ($f(x^{(i)}) = y^{(i)}$)
* $J(1) = \frac{1}{2(3)} \left[ (0)^2 + (0)^2 + (0)^2 \right] = 0$ (Global Minimum)


* **When $w = 0.5$**:
* $J(0.5) = \frac{1}{2(3)} \left[ (0.5 - 1)^2 + (1 - 2)^2 + (1.5 - 3)^2 \right] = \frac{3.5}{6} \approx 0.58$


* **When $w = 0$**:
* $J(0) = \frac{1}{2(3)} \left[ (0 - 1)^2 + (0 - 2)^2 + (0 - 3)^2 \right] = \frac{14}{6} \approx 2.33$


* **When $w = -0.5$**:
* $J(-0.5) = \frac{1}{2(3)} \left[ (-0.5 - 1)^2 + (-1 - 2)^2 + (-1.5 - 3)^2 \right] \approx 5.25$



### Notes

* The horizontal axis of the cost function plot represents the parameter $w$, while the vertical axis represents the total cost value $J(w)$.
* When the straight-line fit $f(x)$ passes closely through data points, the cost $J(w)$ is small; when the line deviates significantly, the cost increases rapidly.
* The optimal parameter $w$ corresponds directly to the lowest point at the bottom of the $J(w)$ U-shaped curve.
* The next video will expand this visualization from a 2D curve into 3D surface and contour plots for models using both parameters $w$ and $b$.

# Video 1.13: Cost Function Visualizations

### Key Concepts

* **3D Surface Plot**: A three-dimensional visualization of the cost function $J(w, b)$ where $w$ and $b$ form the horizontal axes and the height represents the cost value $J$.
* **Contour Plot**: A two-dimensional representation of a 3D cost function created by taking horizontal slices of the surface, where each ellipse (oval) represents a set of points with identical cost values $J(w, b)$.
* **Global Minimum**: The bottom-most point of the bowl-shaped surface (or center of the innermost ellipse on a contour plot) where the cost $J(w, b)$ is minimized.

### Topics Covered

* Re-introducing parameter $b$ alongside $w$ to evaluate the full linear regression model $f_{w,b}(x) = wx + b$
* Visualizing cost functions with two parameters as 3D bowl-shaped (or hammock-shaped) surfaces
* Understanding contour plots using the analogy of topographical maps (e.g., Mount Fuji)
* Connecting individual points on a contour plot $(w, b)$ to their corresponding prediction lines $f(x)$ on a dataset

### Notes

* Adding parameter $b$ expands the 2D U-shaped parabola into a 3D bowl-shaped surface.
* Any single point on the 3D surface or 2D contour plot corresponds to a specific pair of parameters $(w, b)$ and its resulting line fit $f(x)$.
* All points lying on the same ellipse line in a contour plot yield the exact same cost value $J(w, b)$, even though their underlying parameter values $w$ and $b$ differ.
* The center of the innermost concentric oval on a contour plot represents the minimum cost $J(w, b)$, indicating the optimal straight-line fit for the training set.
* The next video will walk through specific choices of parameters $w$ and $b$ on contour plots to show how they affect line fitting on data.
