---
First Created: "10 December 2025"
tags:
  - CS229
---
```table-of-contents
maxLevel:2
```

---
# Chapter 4: Generative Learning Algorithms

### Discriminative Learning Algorithms

Consider a classification problem in which we want to learn to distinguish between elephants ($y = 1$) and dogs ($y = 0$), based on some features of an animal. Given a training set, an algorithm like logistic regression or the perceptron algorithm (basically) tries to find a straight line—that is, a **decision boundary**—that separates the elephants and dogs. Then, to classify a new animal as either an elephant or a dog, it checks on which side of the decision boundary it falls, and makes its prediction accordingly.

Algorithms that try to learn $p(y|x)$ directly (such as logistic regression), or algorithms that try to learn mappings directly from the space of inputs $\mathcal{X}$ to the labels $\{0, 1\}$ (such as the perceptron algorithm) are called **discriminative learning algorithms**.

### Generative Learning Algorithms

Here's a different approach. First, looking at elephants, we can build a **model of what elephants look like**. Then, looking at dogs, we can build a **separate model of what dogs look like**. Finally, to classify a new animal, we can match the new animal against the elephant model, and match it against the dog model, to see whether the new animal looks more like the elephants or more like the dogs we had seen in the training set.

We'll talk about algorithms that instead try to model **$p(x|y)$** (and $p(y)$). These algorithms are called **generative learning algorithms**. For instance, if $y$ indicates whether an example is a dog ($0$) or an elephant ($1$), then $p(x|y = 0)$ models the distribution of dogs' features, and $p(x|y = 1)$ models the distribution of elephants' features.

After modeling $p(y)$ (called the **class priors**) and $p(x|y)$, our algorithm can then use **Bayes rule** to derive the posterior distribution on $y$ given $x$:
$$p(y|x) = \frac{p(x|y)p(y)}{p(x)}$$

Here, the denominator is given by:$$p(x) = p(x|y = 1)p(y = 1) + p(x|y = 0)p(y = 0)$$(you should be able to verify that this is true from the standard properties of probabilities), and thus can also be expressed in terms of the quantities $p(x|y)$ and $p(y)$ that we've learned. 

Actually, if we're calculating $p(y|x)$ in order to make a prediction, then we don't actually need to calculate the denominator, since
$$\arg \max_y p(y|x) = \arg \max_y \frac{p(x|y)p(y)}{p(x)} = \arg \max_y p(x|y)p(y).$$

## 📐 4.1 Gaussian Discriminant Analysis (GDA)

The first generative learning algorithm that we'll look at is **Gaussian Discriminant Analysis (GDA)**.

In this model, we'll assume that $p(x|y)$ is distributed according to a **multivariate normal distribution**.

### 4.1.1 The Multivariate Normal Distribution

The multivariate normal distribution in $d$-dimensions, $\mathcal{N}(\mu, \Sigma)$, is parameterized by:
- A **mean vector** $\mu \in \mathbb{R}^d$.
- A **covariance matrix** $\Sigma \in \mathbb{R}^{d \times d}$, where $\Sigma \ge 0$ is symmetric and positive semi-definite.

Its density is given by:
$$p(x; \mu, \Sigma) = \frac{1}{(2\pi)^{d/2}|\Sigma|^{1/2}} \exp \left( -\frac{1}{2} (x - \mu)^T \Sigma^{-1} (x - \mu) \right)$$
In the equation above, $|\Sigma|$ denotes the determinant of the matrix $\Sigma$.

For a random variable $X$ distributed $\mathcal{N}(\mu, \Sigma)$:

- The **mean** is: $E[X] = \int_x x p(x; \mu, \Sigma)dx = \mu$

- The **covariance** of a vector-valued random variable $Z$ is defined as $\text{Cov}(Z) = E[(Z - E[Z])(Z - E[Z])^T]$. If $X \sim \mathcal{N}(\mu, \Sigma)$, then: $\text{Cov}(X) = \Sigma$

#### Visualizing the Multivariate Gaussian Density

The shape and orientation of the Gaussian density are determined by the covariance matrix $\Sigma$:

> [!blue] Varying $\Sigma = cI$ (Scalar Multiples of Identity):
> ![[Multivariate Gaussian Distribution Density.png]]
> 
> - Left: $\Sigma = I$ (Standard Normal Distribution).
> - Middle: $\Sigma = 0.6I$ (More compressed).
> - Right: $\Sigma = 2I$ (More spread-out).
> 
> As $\Sigma$ becomes larger, the Gaussian becomes more "spread-out," and as it becomes smaller, the distribution becomes more "compressed."

> [!orange] Varying Off-Diagonal Entries (Positive Correlation):
> ![[Pasted image 20251210125417.png]]
> The figures below show Gaussians with mean 0, and with covariance matrices respectively:
> $$\Sigma = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}; \quad \Sigma = \begin{pmatrix} 1 & 0.5 \\ 0.5 & 1 \end{pmatrix}; \quad \Sigma = \begin{pmatrix} 1 & 0.8 \\ 0.8 & 1 \end{pmatrix}$$
> As we increase the off-diagonal entry in $\Sigma$, the density becomes more "compressed" towards the $45^\circ$ line (given by $x_1 = x_2$).
> 
> We can see this more clearly when we look at the contours of the same three densities:
> ![[Pasted image 20251210125546.png]]

> [!green] Varying Off-Diagonal Entries (Negative Correlation) and Unequal Variances:
> ![[Pasted image 20251210125705.png]]   
> $$\Sigma = \begin{pmatrix} 1 & -0.5 \\ -0.5 & 1 \end{pmatrix}; \quad \Sigma = \begin{pmatrix} 1 & -0.8 \\ -0.8 & 1 \end{pmatrix}; \quad \Sigma = \begin{pmatrix} 3 & 0.8 \\ 0.8 & 1 \end{pmatrix}$$
> 
> Decreasing the off-diagonal elements (negative values) compresses the density in the opposite direction.
> 
> More generally, by varying the parameters, the contours will form ellipses (the rightmost figure showing an example).

> [!cyan] Varying $\mu$ (Mean):
> Fixing $\Sigma = I$, by varying $\mu$, we can move the mean of the density around.
> ![[Pasted image 20251210130211.png]]
> 
> The figures above were generated using $\Sigma = I$, and respectively:
> $$\mu = \begin{pmatrix} 1 \\ 0 \end{pmatrix}; \quad \mu = \begin{pmatrix} -0.5 \\ 0 \end{pmatrix}; \quad \mu = \begin{pmatrix} -1 \\ -1.5 \end{pmatrix}$$
 
---
### 4.1.2 The Gaussian Discriminant Analysis Model

When we have a **classification** problem in which the input features $x$ are continuous-valued random variables, the GDA model assumes the following:
$$\begin{aligned} y &\sim \text{Bernoulli}(\phi) \\ x|y = 0 &\sim \mathcal{N}(\mu_0, \Sigma) \\ x|y = 1 &\sim \mathcal{N}(\mu_1, \Sigma) \end{aligned}$$

> Note that this model uses **only one covariance matrix $\Sigma$** shared between the two classes.

Writing out the distributions, this is:
$$\begin{aligned} p(y) &= \phi^y (1 - \phi)^{1-y} \\ p(x|y = 0) &= \frac{1}{(2\pi)^{d/2}|\Sigma|^{1/2}} \exp \left( -\frac{1}{2} (x - \mu_0)^T \Sigma^{-1} (x - \mu_0) \right) \\ p(x|y = 1) &= \frac{1}{(2\pi)^{d/2}|\Sigma|^{1/2}} \exp \left( -\frac{1}{2} (x - \mu_1)^T \Sigma^{-1} (x - \mu_1) \right) \end{aligned}$$

The goal of MLE is to find the parameters ($\phi, \mu_0, \mu_1, \Sigma$) that **maximize the likelihood** of observing the given training data. This is achieved by maximizing the log-likelihood function.

The log-likelihood of the data is given by:
$$\begin{aligned} \ell(\phi, \mu_0, \mu_1, \Sigma) &= \log \prod_{i=1}^n p(x^{(i)}, y^{(i)}; \phi, \mu_0, \mu_1, \Sigma) \\ &= \log \prod_{i=1}^n p(x^{(i)}|y^{(i)}; \mu_0, \mu_1, \Sigma)p(y^{(i)}; \phi) \end{aligned}$$

By maximizing $\ell$ with respect to the parameters, the Maximum Likelihood Estimates (MLE) are found to be:
$$\begin{aligned} \phi &= \frac{1}{n} \sum_{i=1}^n \mathbf{1}\{y^{(i)} = 1\} \\ \mu_0 &= \frac{\sum_{i=1}^n \mathbf{1}\{y^{(i)} = 0\}x^{(i)}}{\sum_{i=1}^n \mathbf{1}\{y^{(i)} = 0\}} \\ \mu_1 &= \frac{\sum_{i=1}^n \mathbf{1}\{y^{(i)} = 1\}x^{(i)}}{\sum_{i=1}^n \mathbf{1}\{y^{(i)} = 1\}} \\ \Sigma &= \frac{1}{n} \sum_{i=1}^n (x^{(i)} - \mu_{y^{(i)}})(x^{(i)} - \mu_{y^{(i)}})^T \end{aligned}$$

>[!info] Pictorially, what the algorithm is doing can be seen in as follows:
>![[Pasted image 20251210131356.png]]
>
>The figure below shows a training set, the contours of the two fitted Gaussian distributions, and the resulting decision boundary.
>
>- The two Gaussians have contours that are the **same shape and orientation** because they share a covariance matrix $\Sigma$. 
>- They have **different means** $\mu_0$ and $\mu_1$.
>- The straight line gives the **decision boundary** where $p(y = 1|x) = 0.5$.

---
### 4.1.3 Discussion: GDA and Logistic Regression

The GDA model has an interesting relationship to logistic regression. If we view the quantity $p(y = 1|x; \phi, \mu_0, \mu_1, \Sigma)$ as a function of $x$, we find that it can be expressed in the form:
$$p(y = 1|x; \phi, \Sigma, \mu_0, \mu_1) = \frac{1}{1 + \exp(-\theta^T x)}$$

This is exactly the form that **logistic regression** (a discriminative algorithm) used to model $p(y = 1|x)$.

#### Choosing between GDA and Logistic Regression


#### GDA: Stronger Assumptions, More Data Efficient

- **GDA** makes ***stronger** modeling assumptions* about the data than does logistic regression.

- **Asymptotic Efficiency:** When this modeling assumptions are correct (i.e., $p(x|y)$ is Gaussian with shared $\Sigma$), GDA is **asymptotically efficient**. This means that in the limit of very large training sets, no algorithm can strictly estimate $p(y|x)$ more accurately than GDA.

- **Data Efficiency:** When its assumptions are correct or approximately correct, GDA will generally find better fits, even for small training set sizes, and is considered **more data efficient** (requires less training data to learn "well").

#### Logistic Regression: Weaker Assumptions, More Robust

- In contrast, by making ***significantly** weaker assumptions*, **logistic regression** is also more robust and less sensitive to incorrect modeling assumptions.

- **Robustness:** It is more robust and less sensitive to incorrect modeling assumptions. For instance, if $x\mid y=0 \sim \text{Poisson}(\lambda_0)$ and $x\mid y=1 \sim \text{Poisson}(\lambda_1)$, $p(y\mid x)$ will still be logistic, and logistic regression will work well.

- **Non-Gaussian Data:** When the data is indeed non-Gaussian, logistic regression will almost always perform better than GDA in the limit of large datasets.


---

## TODO: 📊 4.2 Naive bayes (Option Reading)