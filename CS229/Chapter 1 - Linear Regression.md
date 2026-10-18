---
First Created: 2025-11-26T19:21:00
tags:
  - CS229
---
```table-of-contents
maxLevel:2
```

---
# Chapter 1 - Linear Regression

>[!TLDR] TLDR: Linear Regression
>**What problem it solves**: Linear Regression solves a **Supervised Learning/Regression** problem, specifically predicting a **continuous target variable** $y$ as a **linear function** of input features $\mathbf{x}$. 
>
>**How it solves it**: It seeks to minimize the **squared error** between predictions and actual values (Least-Squares Cost Function $J(\mathbf{\theta})$). Two main variants are:
>- **1. Iterative Method (Gradient Descent):** Starts with an initial guess and repeatedly adjusts $\mathbf{\theta}$ in the direction that steepest decreases the cost $J(\mathbf{\theta})$.
>- **2. Closed-Form Method (Normal Equation):** Directly calculates the optimal $\mathbf{\theta}$ using matrix algebra: $\mathbf{\theta} = (\mathbf{X}^T \mathbf{X})^{-1}\mathbf{X}^T \mathbf{y}$.

### 💻 Representing Functions and the Cost Function

To perform **supervised learning**, we must decide how we're going to represent functions/hypotheses $h$ in a computer. As an initial choice, let's say we decide to approximate $y$ as a **linear function** of $\mathbf{x}$:

$$h_{\theta}(\mathbf{x}) = \theta_0 + \theta_1 x_1 + \theta_2 x_2$$

Here, the $\theta_i$'s are the **parameters** (also called **weights**) parameterizing the space of linear functions mapping from $\mathcal{X}$ to $\mathcal{Y}$. When there is no risk of confusion, we will drop the $\theta$ subscript in $h_{\theta}(\mathbf{x})$, and write it more simply as $h(\mathbf{x})$.

To simplify our notation, we also introduce the convention of letting $x_0 = 1$ (this is the intercept term), so that
$$h_{\theta}(\mathbf{x}) = \sum_{i=0}^{d} \theta_i x_i = \mathbf{\theta}^{T} \mathbf{x},$$

where on the right-hand side above we are viewing $\mathbf{\theta}$ and $\mathbf{x}$ both as vectors, and here $d$ is the number of input variables (not counting $x_0$).


### 📏 Defining the Cost Function

Now, given a training set, how do we pick, or **learn**, the parameters $\mathbf{\theta}$? One reasonable method seems to be to make $h(\mathbf{x})$ close to $y$, at least for the training examples we have. To formalize this, we will define a function that measures, for each value of the $\mathbf{\theta}$'s, how close the $h_{\theta}(\mathbf{x}^{(i)})$'s are to the corresponding $y^{(i)}$'s.

We define the **cost function**:

$$J(\mathbf{\theta}) = \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(\mathbf{x}^{(i)}) - y^{(i)})^2.$$

If you've seen linear regression before, you may recognize this as the familiar **least-squares cost function** that gives rise to the **ordinary least squares regression model**. Whether or not you have seen it previously, let's keep going, and we'll eventually show this to be a special case of a much broader family of algorithms.

---
## 🚀 1.1 LMS Algorithm

We want to choose $\mathbf{\theta}$ so as to minimize $J(\mathbf{\theta})$. To do so, let's use a search algorithm that starts with some "initial guess" for $\mathbf{\theta}$, and that repeatedly changes $\mathbf{\theta}$ to make $J(\mathbf{\theta})$ smaller, until hopefully we converge to a value of $\mathbf{\theta}$ that minimizes $J(\mathbf{\theta})$.

Specifically, let's consider the **gradient descent** algorithm, which starts with some initial $\mathbf{\theta}$, and repeatedly performs the update:

$$\theta_j := \theta_j - \alpha \frac{\partial}{\partial \theta_j} J(\mathbf{\theta})$$

(This update is simultaneously performed for all values of $j = 0, \dots, d$.)

Here, $\alpha$ is called the **learning rate**. This is a very natural algorithm that repeatedly takes a step in the direction of steepest decrease of $J$.

### Calculating the Partial Derivative

In order to implement this algorithm, we have to work out what is the partial derivative term on the right hand side. Let's first work it out for the case of if we have only **one training example** $(\mathbf{x}, y)$, so that we can neglect the sum in the definition of $J$. We have:

$$\begin{aligned} \frac{\partial}{\partial \theta_j} J(\mathbf{\theta}) &= \frac{\partial}{\partial \theta_j} \frac{1}{2} (h_{\mathbf{\theta}}(\mathbf{x}) - y)^2 \\ &= 2 \cdot \frac{1}{2} (h_{\mathbf{\theta}}(\mathbf{x}) - y) \cdot \frac{\partial}{\partial \theta_j} (h_{\mathbf{\theta}}(\mathbf{x}) - y) \\ &= (h_{\mathbf{\theta}}(\mathbf{x}) - y) \cdot \frac{\partial}{\partial \theta_j} \left( \sum_{i=0}^{d} \theta_i x_i - y \right) \\ &= (h_{\mathbf{\theta}}(\mathbf{x}) - y) x_j \end{aligned}$$

### The LMS Update Rule (Single Example)

For a single training example, this gives the update rule:

$$\theta_j := \theta_j + \alpha \left( y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right) x^{(i)}_j.$$

The rule is called the **LMS update rule** (LMS stands for "least mean squares"), and is also known as the **Widrow-Hoff learning rule**. This rule has several properties that seem natural and intuitive. For instance, the magnitude of the update is proportional to the error term $(y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}))$; thus, for instance, if we are encountering a training example on which our prediction nearly matches the actual value of $y^{(i)}$, then we find that there is little need to change the parameters; in contrast, a larger change to the parameters will be made if our prediction $h_{\mathbf{\theta}}(\mathbf{x}^{(i)})$ has a large error (i.e., if it is very far from $y^{(i)}$).

### 📦 Batch Gradient Descent

We'd derived the LMS rule for when there was only a single training example. There are two ways to modify this method for a training set of more than one example. The first is replace it with the following algorithm:

$\text{Repeat until convergence}$ {
$$\theta_j := \theta_j + \alpha \sum_{i=1}^{n} \left( y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right) x^{(i)}_j, \quad \text{(for every } j)$$
}

By grouping the updates of the coordinates into an update of the vector $\mathbf{\theta}$, we can rewrite the update in a slightly more succinct way:
$$\mathbf{\theta} := \mathbf{\theta} + \alpha \sum_{i=1}^{n} \left( y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right) \mathbf{x}^{(i)}$$

The reader can easily verify that the quantity in the summation in the update rule above is just $\partial J(\mathbf{\theta}) / \partial \theta_j$ (for the original definition of $J$). 

So, this is simply gradient descent on the original cost function $J$. This method looks at every example in the entire training set on every step, and is called **batch gradient descent**.

### 🔁 Stochastic Gradient Descent (SGD)

There is an alternative to batch gradient descent that also works very well, called **stochastic gradient descent** (also incremental gradient descent).

Consider the following algorithm:

$$
\begin{aligned}
\text{Loop } \{ \\ &
\quad \text{for } i = 1 \text{ to } n, \{ \\ & \\ &
\qquad\quad \theta_j := \theta_j + \alpha \left( y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right) x^{(i)}_j, 
\quad \text{(for every } j)\\ & \\ &
\quad \} \\
\}
\end{aligned}
$$

By grouping the updates of the coordinates into an update of the vector $\mathbf{\theta}$, we can rewrite update in a slightly more succinct way:
$$\mathbf{\theta} := \mathbf{\theta} + \alpha \left( y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right) \mathbf{x}^{(i)}$$

### Comparison with Batch Gradient Descent

- **Batch Gradient Descent** has to scan through the **entire training set** ($n$ examples) before taking a single step—a costly operation if $n$ is large.

- **Stochastic Gradient Descent** can start making progress right away, and continues to make progress with **each example** it looks at.    

Often, stochastic gradient descent gets $\mathbf{\theta}$ "close" to the minimum much faster than batch gradient descent. 

![[Pasted image 20251202154019.png]]

While SGD may never "converge" exactly to the minimum and the parameters $\mathbf{\theta}$ will keep oscillating around the minimum of $J(\mathbf{\theta})$, in practice, the values near the minimum are usually reasonably good approximations. For these reasons, particularly when the training set is **large**, stochastic gradient descent is often **preferred** over batch gradient descent.

---
## 📐 1.2.2 The Normal Equation

We can use matrix derivatives to find the value of the parameter vector $\mathbf{\theta}$ that minimizes the cost function $J(\mathbf{\theta})$ in a **closed-form** solution.
### Matrix-Vectorial Notation

First, we rewrite the cost function $J(\mathbf{\theta})$ using matrix and vector notation:

1. **Design Matrix $\mathbf{X}$**: This is an $n \times (d+1)$ matrix containing all training examples, where $n$ is the number of examples and $(d+1)$ includes the $d$ features plus the intercept term $x_0=1$.
   $$\mathbf{X} = \begin{bmatrix} — (\mathbf{x}^{(1)})^T — \\ — (\mathbf{x}^{(2)})^T — \\ \vdots \\ — (\mathbf{x}^{(n)})^T — \end{bmatrix}$$

2. **Target Vector $\mathbf{y}$**: This is an $n$-dimensional vector containing all target values.
  $$\mathbf{y} = \begin{bmatrix} y^{(1)} \\ y^{(2)} \\ \vdots \\ y^{(n)} \end{bmatrix}$$

Since the hypothesis for a single example is $h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) = (\mathbf{x}^{(i)})^T \mathbf{\theta}$, the vector of all predictions is $\mathbf{X}\mathbf{\theta}$. The vector of errors is $\mathbf{X}\mathbf{\theta} - \mathbf{y}$:

$$\mathbf{X}\mathbf{\theta} - \mathbf{y} = \begin{bmatrix} (\mathbf{x}^{(1)})^T \mathbf{\theta} \\ \vdots \\ (\mathbf{x}^{(n)})^T \mathbf{\theta} \end{bmatrix} - \begin{bmatrix} y^{(1)} \\ \vdots \\ y^{(n)} \end{bmatrix} = \begin{bmatrix} h_{\mathbf{\theta}}(\mathbf{x}^{(1)}) - y^{(1)} \\ \vdots \\ h_{\mathbf{\theta}}(\mathbf{x}^{(n)}) - y^{(n)} \end{bmatrix}$$

Using the fact that for a vector $\mathbf{z}$, $\mathbf{z}^T \mathbf{z} = \sum_{i} z_i^2$, the cost function $J(\mathbf{\theta})$ can be written as:

$$J(\mathbf{\theta}) = \frac{1}{2} \sum_{i=1}^{n} (h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) - y^{(i)})^2 = \frac{1}{2} (\mathbf{X}\mathbf{\theta} - \mathbf{y})^T (\mathbf{X}\mathbf{\theta} - \mathbf{y})$$
### Deriving the Normal Equation

To minimize $J(\mathbf{\theta})$, we find its gradient with respect to $\mathbf{\theta}$ and set it to zero.

The gradient is calculated as follows:

$$\begin{aligned} \nabla_{\mathbf{\theta}} J(\mathbf{\theta}) &= \nabla_{\mathbf{\theta}} \frac{1}{2} (\mathbf{X}\mathbf{\theta} - \mathbf{y})^T (\mathbf{X}\mathbf{\theta} - \mathbf{y}) \\ &= \frac{1}{2} \nabla_{\mathbf{\theta}} \left[ (\mathbf{X}\mathbf{\theta})^T \mathbf{X}\mathbf{\theta} - (\mathbf{X}\mathbf{\theta})^T \mathbf{y} - \mathbf{y}^T (\mathbf{X}\mathbf{\theta}) + \mathbf{y}^T \mathbf{y} \right] \\ &= \frac{1}{2} \nabla_{\mathbf{\theta}} \left[ \mathbf{\theta}^T (\mathbf{X}^T \mathbf{X}) \mathbf{\theta} - \mathbf{y}^T (\mathbf{X}\mathbf{\theta}) - \mathbf{y}^T (\mathbf{X}\mathbf{\theta}) \right] \\ &= \frac{1}{2} \nabla_{\mathbf{\theta}} \left[ \mathbf{\theta}^T (\mathbf{X}^T \mathbf{X}) \mathbf{\theta} - 2 (\mathbf{X}^T \mathbf{y})^T \mathbf{\theta} \right] \\ &= \frac{1}{2} \left[ 2 \mathbf{X}^T \mathbf{X} \mathbf{\theta} - 2 \mathbf{X}^T \mathbf{y} \right] \\ &= \mathbf{X}^T \mathbf{X} \mathbf{\theta} - \mathbf{X}^T \mathbf{y} \end{aligned}$$

Setting the derivative to zero, $\nabla_{\mathbf{\theta}} J(\mathbf{\theta}) = 0$, yields the normal equation:

$$\mathbf{X}^T \mathbf{X} \mathbf{\theta} = \mathbf{X}^T \mathbf{y}$$

### Closed-Form Solution

Solving the normal equation for $\mathbf{\theta}$ gives the closed-form solution that minimizes $J(\mathbf{\theta})$:

$$\mathbf{\theta} = (\mathbf{X}^T \mathbf{X})^{-1}\mathbf{X}^T \mathbf{y}$$

This formula allows you to calculate the optimal parameters $\mathbf{\theta}$ directly, without the need for an iterative optimization algorithm like Gradient Descent.

---
## 🎲 1.3 Probabilistic Interpretation: Maximum Likelihood Estimation

The least-squares cost function, $J(\mathbf{\theta})$, is a reasonable choice for linear regression because it can be derived directly from a set of **probabilistic assumptions** using the principle of **Maximum Likelihood Estimation (MLE)**.

### Probabilistic Assumptions

We make two key assumptions about the relationship between the target variable $y^{(i)}$ and the input features $\mathbf{x}^{(i)}$:

1. **Linear Relationship with Error**: The target variable is a linear function of the inputs plus an error term $\epsilon^{(i)}$:
$$y^{(i)} = \mathbf{\theta}^T \mathbf{x}^{(i)} + \epsilon^{(i)}$$
	The term $\epsilon^{(i)}$ captures unmodeled effects or random noise.

2. **Gaussian (Normal) Error Distribution**: The error terms $\epsilon^{(i)}$ are IID (Independently and Identically Distributed) according to a Gaussian distribution with mean zero and variance $\sigma^2$.
$$\epsilon^{(i)} \sim \mathcal{N}(0, \sigma^2)$$

This second assumption implies that the conditional distribution of $y^{(i)}$ given $\mathbf{x}^{(i)}$ is also Gaussian, centered at the linear prediction $h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) = \mathbf{\theta}^T \mathbf{x}^{(i)}$:

$$p(y^{(i)} | \mathbf{x}^{(i)}; \mathbf{\theta}) = \frac{1}{\sqrt{2\pi}\sigma} \exp \left( - \frac{(y^{(i)} - \mathbf{\theta}^T \mathbf{x}^{(i)})^2}{2\sigma^2} \right)$$

(Note: $\mathbf{\theta}$ is treated as a fixed parameter, not a random variable, so we use a semi-colon in the conditioning: $\mathbf{y}^{(i)} | \mathbf{x}^{(i)}; \mathbf{\theta}$).

### The Likelihood Function

Given the IID assumption, the probability of the entire dataset (the **likelihood function**) is the product of the individual probabilities:
$$L(\mathbf{\theta}) = L(\mathbf{\theta}; \mathbf{X}, \mathbf{y}) = p(\mathbf{y} | \mathbf{X}; \mathbf{\theta}) = \prod_{i=1}^{n} p(y^{(i)} | \mathbf{x}^{(i)}; \mathbf{\theta})$$

Substituting the Gaussian density:
$$L(\mathbf{\theta}) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi}\sigma} \exp \left( - \frac{(y^{(i)} - \mathbf{\theta}^T \mathbf{x}^{(i)})^2}{2\sigma^2} \right)$$

### Maximum Likelihood Estimation

The **principal of maximum likelihood** states that we should choose the parameters $\mathbf{\theta}$ that maximize the likelihood $L(\mathbf{\theta})$, making the observed data as probable as possible.

Instead of maximizing $L(\mathbf{\theta})$, the derivations will be a bit simpler if we maximize the **log-likelihood** $\ell(\mathbf{\theta})$, as $\log$ is a strictly increasing function:

$$\begin{aligned} \ell(\mathbf{\theta}) &= \log L(\mathbf{\theta}) \\ &= \sum_{i=1}^{n} \log \left[ \frac{1}{\sqrt{2\pi}\sigma} \exp \left( - \frac{(y^{(i)} - \mathbf{\theta}^T \mathbf{x}^{(i)})^2}{2\sigma^2} \right) \right] \\ &= \sum_{i=1}^{n} \left[ \log \left( \frac{1}{\sqrt{2\pi}\sigma} \right) - \frac{(y^{(i)} - \mathbf{\theta}^T \mathbf{x}^{(i)})^2}{2\sigma^2} \right] \\ &= n \log \left( \frac{1}{\sqrt{2\pi}\sigma} \right) - \frac{1}{\sigma^2} \cdot \frac{1}{2} \sum_{i=1}^{n} (y^{(i)} - \mathbf{\theta}^T \mathbf{x}^{(i)})^2 \end{aligned}$$

### Conclusion

To maximize $\ell(\mathbf{\theta})$, we must **minimize** the final term, since the leading terms $n \log (1/\sqrt{2\pi}\sigma)$ and $1/\sigma^2$ are constants with respect to $\mathbf{\theta}$, and the term being minimized is preceded by a negative sign.

The term that must be minimized is:

$$\frac{1}{2} \sum_{i=1}^{n} (y^{(i)} - \mathbf{\theta}^T \mathbf{x}^{(i)})^2$$

This is precisely **$J(\mathbf{\theta})$, our original least-squares cost function❗👀**.

Therefore, under the assumption of **IID Gaussian noise**, **least-squares regression** is equivalent to finding the **maximum likelihood estimate** of the parameters $\mathbf{\theta}$.

---

## 📍 1.4 Locally Weighted Linear Regression (LWR)

The choice of features is critical in standard linear regression, as an inadequate model choice can lead to **underfitting** (left figure: model misses data structure) or an overly complex model can lead to **overfitting** (right figure: model fits noise).

![[Pasted image 20251126190328.png]]

Locally Weighted Linear Regression (LWR) is an algorithm that addresses this feature selection issue by making the choice of features less critical, provided there is sufficient training data.

### LWR Algorithm

Standard linear regression fits a single set of parameters $\mathbf{\theta}$ to minimize the total squared error across **all** training examples and uses that $\mathbf{\theta}$ for future predictions.

In contrast, LWR computes a **new** set of parameters $\mathbf{\theta}$ for **every single query point** $\mathbf{x}$ where a prediction is needed.

For a prediction at a query point $\mathbf{x}$, the LWR algorithm performs the following steps:

1. Fit $\mathbf{\theta}$ to minimize the weighted cost function:
$$\mathbf{\theta} = \arg\min_{\mathbf{\theta}} \sum_{i} w^{(i)} (y^{(i)} - \mathbf{\theta}^T \mathbf{x}^{(i)})^2$$

2. **Output** the prediction: $\mathbf{\theta}^T \mathbf{x}$.

### The Weight Function

The $w^{(i)}$'s are non-negative weights that emphasize training examples closer to the query point $\mathbf{x}$. The standard choice for the weights is:

$$w^{(i)} = \exp \left( - \frac{(\mathbf{x}^{(i)} - \mathbf{x})^2}{2\tau^2} \right)$$

(If $\mathbf{x}$ is vector-valued, the term $(\mathbf{x}^{(i)} - \mathbf{x})^2$ becomes the squared Euclidean distance $(\mathbf{x}^{(i)} - \mathbf{x})^T (\mathbf{x}^{(i)} - \mathbf{x})$).

- If the training example $\mathbf{x}^{(i)}$ is **close** to the query point $\mathbf{x}$ (i.e., $|\mathbf{x}^{(i)} - \mathbf{x}|$ is small), then $w^{(i)}$ is close to $\mathbf{1}$. The error on this point is weighted highly.

- If $\mathbf{x}^{(i)}$ is **far** from $\mathbf{x}$ (i.e., $|\mathbf{x}^{(i)} - \mathbf{x}|$ is large), then $w^{(i)}$ is small. The error on this point is largely ignored.

The parameter $\tau$ is called the **bandwidth parameter** and controls how quickly the weight falls off with distance. A smaller $\tau$ means the model only considers points extremely close to $\mathbf{x}$.

### 💡 Parametric vs. Non-Parametric Algorithms

LWR is the first example of a **non-parametric algorithm** we encounter.

- **Parametric Learning Algorithm (e.g., Unweighted Linear Regression):**
	
    - Has a **fixed, finite number of parameters** ($\mathbf{\theta}$'s), regardless of the training set size $n$.
    - Once $\mathbf{\theta}$ is fit, the training data can be discarded for future predictions.

- **Non-Parametric Learning Algorithm (e.g., LWR):**
	
    - The term “non-parametric” (roughly) refers to the fact that the amount of information needed to represent the hypothesis $h$ **grows linearly** with the size of the training set $n$.
    
    - To make a prediction, the algorithm **requires the entire training set** to be kept, as it calculates new parameters $\mathbf{\theta}$ every time based on the distance to $\mathbf{x}$.

---
