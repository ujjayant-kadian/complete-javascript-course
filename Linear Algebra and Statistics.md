## 1. Linear Algebra

### 1.1. Vectors and Matrices
- **Vectors** are one-dimensional arrays of numbers. In machine learning, they can represent data points, features, or weights.
  - A vector can be denoted as \( \mathbf{v} = [v_1, v_2, \ldots, v_n] \), where each element represents a different dimension.
- **Matrices** are two-dimensional arrays of numbers organized in rows and columns. Matrices are often used for representing datasets, where rows correspond to observations and columns correspond to features.
  - A matrix \( \mathbf{A} \) of dimensions \( m \times n \) has \( m \) rows and \( n \) columns: 
    \[
    \mathbf{A} = \begin{bmatrix}
    a_{11} & a_{12} & \cdots & a_{1n} \\
    a_{21} & a_{22} & \cdots & a_{2n} \\
    \vdots & \vdots & \ddots & \vdots \\
    a_{m1} & a_{m2} & \cdots & a_{mn}
    \end{bmatrix}
    \]

#### Vector Operations
- **Addition and Subtraction**: You can add or subtract two vectors of the same dimension by performing element-wise addition or subtraction.
  \[
  \mathbf{u} + \mathbf{v} = [u_1 + v_1, u_2 + v_2, \ldots, u_n + v_n]
  \]
- **Scalar Multiplication**: Multiplying a vector by a scalar stretches or shrinks its magnitude.
  \[
  c \mathbf{v} = [c v_1, c v_2, \ldots, c v_n]
  \]
- **Dot Product**: The dot product of two vectors \( \mathbf{u} \) and \( \mathbf{v} \) is a scalar given by:
  \[
  \mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^n u_i v_i
  \]
  It represents the cosine of the angle between two vectors and measures similarity in machine learning.

#### Matrix Operations
- **Matrix Addition and Subtraction**: These operations are performed element-wise and require matrices of the same dimensions.
- **Scalar Multiplication**: Multiplying each element of a matrix by a scalar.
- **Matrix Multiplication**: If \( \mathbf{A} \) is of size \( m \times n \) and \( \mathbf{B} \) is of size \( n \times p \), then the resulting matrix \( \mathbf{C} = \mathbf{A} \mathbf{B} \) will be of size \( m \times p \). The element at \( c_{ij} \) is calculated as:
  \[
  c_{ij} = \sum_{k=1}^n a_{ik} b_{kj}
  \]
- **Transpose**: The transpose of a matrix \( \mathbf{A} \), denoted \( \mathbf{A}^T \), is obtained by swapping its rows and columns.

### 1.2. Determinants and Inverses
- **Determinant**: A scalar value representing a matrix, used in solving linear equations and finding matrix inverses. For a 2x2 matrix:
  \[
  \text{det}(\mathbf{A}) = a_{11} a_{22} - a_{12} a_{21}
  \]
- **Inverse**: The inverse of a matrix \( \mathbf{A} \), denoted \( \mathbf{A}^{-1} \), satisfies \( \mathbf{A} \mathbf{A}^{-1} = \mathbf{I} \), where \( \mathbf{I} \) is the identity matrix. The inverse is used for solving linear systems.

### 1.3. Eigenvalues and Eigenvectors
- An **eigenvector** of a matrix \( \mathbf{A} \) is a vector \( \mathbf{v} \) such that:
  \[
  \mathbf{A} \mathbf{v} = \lambda \mathbf{v}
  \]
  where \( \lambda \) is a scalar known as the **eigenvalue**. Eigenvectors and eigenvalues are important for dimensionality reduction techniques like PCA.

## 2. Statistics

### 2.1. Descriptive Statistics
- **Mean** (average): 
  \[
  \text{Mean} = \frac{1}{n} \sum_{i=1}^n x_i
  \]
- **Median**: The middle value in a sorted dataset.
- **Mode**: The value that appears most frequently.
- **Variance**: Measures the spread of data points:
  \[
  \text{Variance} = \frac{1}{n} \sum_{i=1}^n (x_i - \text{Mean})^2
  \]
- **Standard Deviation**: The square root of the variance, showing the dispersion of data points from the mean.

### 2.2. Probability Distributions
- **Normal Distribution**: A bell-shaped curve characterized by its mean \( \mu \) and standard deviation \( \sigma \):
  \[
  f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x - \mu)^2}{2 \sigma^2}}
  \]
  It is crucial in many machine learning algorithms, including linear regression.
- **Bernoulli Distribution**: Models binary outcomes (0 or 1), with probability \( p \) of success.
- **Binomial Distribution**: Represents the number of successes in \( n \) independent trials.
- **Poisson Distribution**: Models the number of times an event occurs in a fixed interval of time or space.

### 2.3. Covariance and Correlation
- **Covariance** measures how two variables change together:
  \[
  \text{Cov}(X, Y) = \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})
  \]
- **Correlation** is a standardized measure of covariance:
  \[
  \text{Correlation}(X, Y) = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y}
  \]
  It ranges from -1 to 1, indicating the strength and direction of the relationship between variables.

## 3. Probability Theory

### 3.1. Basic Concepts
- **Probability**: The likelihood of an event occurring, ranging from 0 (impossible) to 1 (certain).
- **Sample Space**: The set of all possible outcomes.
- **Event**: A subset of the sample space.
- **Conditional Probability**: The probability of an event \( A \) occurring given that \( B \) has occurred:
  \[
  P(A|B) = \frac{P(A \cap B)}{P(B)}
  \]
- **Bayes' Theorem**: Provides a way to update probabilities based on new information:
  \[
  P(A|B) = \frac{P(B|A) P(A)}{P(B)}
  \]

### 3.2. Random Variables and Expected Value
- A **random variable** assigns numerical values to outcomes of a random process.
- **Expected Value** \( E(X) \) is the weighted average of all possible values:
  \[
  E(X) = \sum_{i=1}^n x_i P(x_i)
  \]

### 3.3. Law of Large Numbers and Central Limit Theorem
- **Law of Large Numbers**: As the number of trials increases, the average of the results gets closer to the expected value.
- **Central Limit Theorem**: The sum of a large number of independent random variables approaches a normal distribution, regardless of the original distribution.

## 4. Mathematics for Machine Learning

### 4.1. Calculus
- **Derivatives**: Measure the rate of change of a function.
  - In machine learning, derivatives are used in gradient descent to optimize cost functions.
- **Partial Derivatives**: Derivatives of functions with multiple variables.
  - The **gradient** is a vector of partial derivatives, representing the direction of the steepest ascent.
- **Chain Rule**: Used to compute derivatives of composite functions, crucial for backpropagation in neural networks.

### 4.2. Optimization
- Optimization involves finding the minimum or maximum of a function.
- **Gradient Descent**: An iterative algorithm used to minimize a cost function by updating the parameters in the opposite direction of the gradient.

### 4.3. Functions and Transformations
- **Linear Functions**: Functions of the form \( f(x) = ax + b \), where \( a \) and \( b \) are constants.
- **Nonlinear Functions**: Functions where the rate of change is not constant, often requiring more sophisticated optimization techniques.
- **Logarithmic and Exponential Functions**: These are frequently used in machine learning, particularly in logistic regression and when dealing with growth rates or

 probabilities.

### 4.4. Multivariable Calculus
- Used to optimize functions with multiple inputs (multidimensional data).
- **Hessian Matrix**: A square matrix of second-order partial derivatives used to analyze the curvature of multivariable functions.

## 5. Connecting to Machine Learning

### 5.1. Linear Regression
- Uses a linear model to predict an output based on input features. The equation can be written as:
  \[
  y = \mathbf{w}^T \mathbf{x} + b
  \]
  where \( \mathbf{w} \) is the vector of weights, and \( b \) is the bias term.
- Optimization techniques like gradient descent are used to find the best weights that minimize the loss function.

### 5.2. Classification
- Algorithms like logistic regression use probabilities and the logistic function:
  \[
  \sigma(z) = \frac{1}{1 + e^{-z}}
  \]
  to predict class probabilities.

### 5.3. Dimensionality Reduction
- Techniques like PCA rely on linear algebra concepts such as eigenvectors and eigenvalues to reduce the number of features while preserving the variance.

### 5.4. Neural Networks
- Use calculus for backpropagation, linear algebra for manipulating weights and inputs, and optimization techniques to adjust the model parameters.

### 5.5. Bayesian Methods
- Use probability theory, particularly Bayes' theorem, to update the probability of hypotheses as more data becomes available.

---