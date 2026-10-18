---
tags:
  - CS229
First Created: 2025-12-02T10:47:00
---
---
```table-of-contents
maxLevel:2
```
---

# Chapter 2 - Classification and logistic regression

Let’s now talk about the classification problem. This is just like the regression problem, except that the values y we now want to predict take on only a small number of discrete values.

For now, we will focus on the **binary classification problem**: $y$ can take on only two values, $0$ and $1$.

---
## 📈 2.1 Logistic Regression

> We could approach the classification problem ignoring the fact that y is discrete-valued, and use our old linear regression algorithm to try to predict $y$ given $x$. 

However, it is easy to construct examples where this method performs very poorly:

![[Pasted image 20251202113010.png]]

For instance, in problems like XOR (where classes are not linearly separable) linear regression tends to predict nearly the same value for every input, completely failing to separate the classes. This highlights the need for a hypothesis function better aligned with classification tasks.

>[!info] Ignoring the fact that y is discrete-valued
>
>In a classification problem where the target variable is discrete, $y \in \{0, 1\}$, using standard linear regression (where $h_{\mathbf{\theta}}(\mathbf{x})$ can take any value) is not appropriate.
>
>To address this, we choose a new form for the hypothesis function $h_{\mathbf{\theta}}(\mathbf{x})$ that constrains the output to be between 0 and 1. -> (e.g. **sigmoid**)

### The Sigmoid Hypothesis

We define the hypothesis for logistic regression using the **logistic function** (or **sigmoid function**), $g(z)$:
$$h_{\mathbf{\theta}}(\mathbf{x}) = g(\mathbf{\theta}^\top \mathbf{x}) = \frac{1}{1 + e^{-\mathbf{\theta}^\top \mathbf{x}}}$$
where
$$g(z) = \frac{1}{1 + e^{-z}}$$

The sigmoid function $g(z)$ approaches $1$ as $z \to \infty$ and approaches $0$ as $z \to -\infty$, ensuring that $h(\mathbf{x})$ is always bounded between $0$ and $1$. As before, we assume the convention $x_0 = 1$, so that $\mathbf{\theta}^\top \mathbf{x} = \theta_0 + \sum_{j=1}^{d} \theta_j x_j$.

> [!tip] Derivative of the Sigmoid Function
> A useful property for the derivative of $g(z)$ is:
> 
> $$
> \begin{align}
> g'(z) &= \frac{d}{dz}\left(\frac{1}{1 + e^{-z}}\right) \\
> &= \frac{1}{(1 + e^{-z})^2} \cdot e^{-z} \\
> &= \frac{1}{1 + e^{-z}} \left(1 - \frac{1}{1 + e^{-z}}\right) \\
> &= g(z)(1 - g(z))
> \end{align}
> 
> $$
> 

---
> So, given the logistic regression model, how do we fit $θ$ for it? 
> 
> Following how we saw least squares regression could be derived as the maximum likelihood estimator under a set of assumptions, let’s endow our classification model with a set of probabilistic assumptions, and then fit the parameters via maximum likelihood.

### Probabilistic Interpretation

We model the classification problem using a set of probabilistic assumptions, allowing us to find the parameters $\mathbf{\theta}$ via **Maximum Likelihood Estimation (MLE)**.

We assume that $h_{\mathbf{\theta}}(\mathbf{x})$ represents the probability that the output $y$ is 1:
$$P(y = 1 \mid \mathbf{x}; \mathbf{\theta}) = h_{\mathbf{\theta}}(\mathbf{x})$$
$$P(y = 0 \mid \mathbf{x}; \mathbf{\theta}) = 1 - h_{\mathbf{\theta}}(\mathbf{x})$$

This can be written compactly as a **Bernoulli distribution** ($y \in \{0, 1\}$):
$$p(y \mid \mathbf{x}; \mathbf{\theta}) = (h_{\mathbf{\theta}}(\mathbf{x}))^y (1 - h_{\mathbf{\theta}}(\mathbf{x}))^{1-y}$$

#### The Log-Likelihood Function

Assuming the $n$ training examples are independent, the **likelihood function** is the product of the individual probabilities:
$$L(\mathbf{\theta}) = p(\mathbf{y} \mid \mathbf{X}; \mathbf{\theta}) = \prod_{i=1}^{n} p(y^{(i)} \mid \mathbf{x}^{(i)}; \mathbf{\theta}) = \prod_{i=1}^{n} \left( h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right)^{y^{(i)}} \left( 1 - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right)^{1-y^{(i)}}$$

As before, it will be easier to maximize the log likelihood $\ell(\mathbf{\theta})$ ($\log$ is a strictly increasing function):
$$\ell(\mathbf{\theta}) = \log L(\mathbf{\theta}) = \sum_{i=1}^{n} \left[ y^{(i)} \log h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) + (1 - y^{(i)}) \log(1 - h_{\mathbf{\theta}}(\mathbf{x}^{(i)})) \right]$$

> How do we maximize the likelihood? Similar to our derivation in the case of linear regression, we can use gradient ascent. 
> 
> (Note: in linear regression we minimize error -> gradient DESCENT, here we maximize likelihood -> gradient DESCENT)
#### Gradient Ascent Update Rule

Since we are maximizing $\ell(\mathbf{\theta})$, we use **gradient ascent**. Written in vectorial notation, our updates will therefore be given by $\mathbf{\theta} := \mathbf{\theta} + \alpha \nabla_{\mathbf{\theta}} \ell(\mathbf{\theta})$.

The goal now is to find the gradient for the **stochastic gradient ascent** rule $\nabla_{\mathbf{\theta}} \ell(\mathbf{\theta})$.

To simplify, we work with only one training example $(x, y)$, we compute the partial derivative:
$$\begin{aligned} \frac{\partial}{\partial \theta_j} \ell(\mathbf{\theta}) &= \left[ \frac{y}{g(\mathbf{\theta}^\top \mathbf{x})} - \frac{1 - y}{1 - g(\mathbf{\theta}^\top \mathbf{x})} \right] \frac{\partial}{\partial \theta_j} g(\mathbf{\theta}^\top \mathbf{x}) \\ &= \left[ \frac{y}{g(\mathbf{\theta}^\top \mathbf{x})} - \frac{1 - y}{1 - g(\mathbf{\theta}^\top \mathbf{x})} \right] g(\mathbf{\theta}^\top \mathbf{x})(1 - g(\mathbf{\theta}^\top \mathbf{x})) \frac{\partial}{\partial \theta_j} \mathbf{\theta}^\top \mathbf{x} \\ &= \left[ y(1 - g(\mathbf{\theta}^\top \mathbf{x})) - (1 - y)g(\mathbf{\theta}^\top \mathbf{x}) \right] x_j \\ &= (y - g(\mathbf{\theta}^\top \mathbf{x})) x_j \\ &= (y - h_{\mathbf{\theta}}(\mathbf{x})) x_j \end{aligned}$$

>[!tip]- Computing the partial derivative
>![[Pasted image 20251202132511.png]]

This yields the Stochastic Gradient Ascent update rule for logistic regression:
$$\theta_j := \theta_j + \alpha \left( y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right) x^{(i)}_j$$

If we compare this to the LMS update rule, we see that it looks identical; but this is not the same algorithm, because $h_{\mathbf{\theta}}(\mathbf{x}^{(i)})$ is now defined as a non-linear function of $\mathbf{\theta}^\top \mathbf{x}^{(i)}$.

Nonetheless, it’s a little surprising that we end up with the same update rule for a rather different algorithm and learning problem. Is this coincidence, or is there a deeper reason behind this? We’ll answer this when we get to GLM models.

---
### Alternative Viewpoint: Logistic Loss

The negative log-likelihood (what we minimize) can be viewed using the **logistic loss** $\ell_{\text{logistic}}(t, y)$, where $t = \mathbf{\theta}^\top \mathbf{x}$:
$$\ell_{\text{logistic}}(t, y) \triangleq y \log(1 + e^{-t}) + (1 - y) \log(1 + e^{t})$$

The negative log-likelihood is then:
$$-\ell(\mathbf{\theta}) = \ell_{\text{logistic}}(\mathbf{\theta}^\top \mathbf{x}, y)$$
where oftentimes $t = \mathbf{\theta}^\top \mathbf{x}$ is called the **logit**.

The derivative of the loss with respect to $t$ is:
$$\begin{align}
\frac{\partial \, \text{logistic}(t, y)}{\partial t} 
&= y \frac{-\exp(-t)}{1 + \exp(-t)} 
+ (1 - y) \frac{1}{1 + \exp(-t)} \\[6pt]
&= \frac{1}{1 + \exp(-t)} - y
\end{align}$$

Using the chain rule, this confirms the gradient derived earlier:
$$\frac{\partial}{\partial \theta_j} \ell(\mathbf{\theta}) = - \frac{\partial \ell_{\text{logistic}}(t, y)}{\partial t} \cdot \frac{\partial t}{\partial \theta_j} = - \left( \frac{1}{1 + e^{-t}} - y \right) \cdot x_j = (y - h_{\mathbf{\theta}}(\mathbf{x})) x_j$$

---
## 🧠 2.2 Digression: The Perceptron Learning Algorithm

### The Perceptron Model

We now digress to talk briefly about an algorithm that’s of some historical interest, and that we will also return to later when we talk about learning theory. 

Consider modifying the logistic regression method to “force” it to output values that are either 0 or 1 or exactly.

The perceptron uses a modified hypothesis function $h_{\mathbf{\theta}}(\mathbf{x})$, where the sigmoid function $g(z)$ is replaced by a **threshold function**:
$$g(z) = \begin{cases} 1 & \text{if } z \geq 0 \\ 0 & \text{if } z < 0 \end{cases}$$
The term $\mathbf{\theta}^\top \mathbf{x}$ is the linear score, and the threshold function immediately maps this score to a binary prediction: **1** if the score is non-negative, and **0** otherwise.

If we then let $h_{\mathbf{\theta}}(\mathbf{x}) = g(\mathbf{\theta}^\top \mathbf{x})$ as before but using this modified definition of $g$, and if we use the  update rule:
$$\theta_j := \theta_j + \alpha \left( y^{(i)} - h_{\mathbf{\theta}}(\mathbf{x}^{(i)}) \right) x^{(i)}_j$$

then we have the **perceptron learning algorithm**.

>[!info] Key Differences and Historical Context
> 
> - **Historical Significance:** The perceptron, developed in the 1960s, was an early model intended to represent how individual **neurons** in the brain might function.
> ---
> - **Fundamental Difference:** Although the update rule is cosmetically identical to both the LMS (linear regression) and logistic regression update rules, the perceptron is a very different type of algorithm.
> ---
> - **Probabilistic Interpretation:** Unlike linear regression (which is MLE under Gaussian noise) and logistic regression (which is MLE under a Bernoulli distribution), it is **difficult to assign a meaningful probabilistic interpretation** to the perceptron's predictions or to derive it as a **Maximum Likelihood Estimation** algorithm.

---
## 📊 2.3 Multi-Class Classification

Consider a classification problem in which the response variable $y$ can take on any one of $k$ values, so $y ∈ \{1, 2, \dots , k\}$. The label/response variable is still discrete, but can now take on more than two values. We will thus model it as distributed according to a **multinomial distribution**.

In this case, $p(y \mid x; \theta)$ is a distribution over $k$ possible discrete outcomes and is thus a multinomial distribution. Recall that a multinomial distribution involves $k$ numbers $\phi_1, \dots, \phi_k$ specifying the probability of each of the outcomes. Note that these numbers must satisfy $\sum_{i=1}^{k} \phi_i = 1$. We will design a parameterized model that outputs $\phi_1, \dots, \phi_k$  satisfying this constraint given the input $x$.

### The Softmax Function

We introduce $k$ parameter vectors, $\mathbf{\theta}_1, \dots, \mathbf{\theta}_k$, where $\mathbf{\theta}_j \in \mathbb{R}^d$. 

Intuitively, we would like to use $\mathbf{\theta}_1^\top x, \dots, \mathbf{\theta}_k^\top x$ to represent $\phi_1, \dots, \phi_k$, the probabilities  $P(y = 1 | x; θ), \dots , P(y = k | x; θ)$.

However, there are two issues with such a direct approach:
- First, $\theta_j^\top x$ is not necessarily within $[0,1]$. 
- Second, the summation of $\theta_j^\top x$'s is not necessarily $1$. 

> Thus, instead, we use the **softmax function** to turn the logits  $\mathbf{t} = (t_1, \dots, t_k) = (\theta_1^\top x, \ldots, \theta_k^\top x)$ into a **probability vector** $\mathbf{\phi} = (\phi_1, \dots, \phi_k)$ with nonnegative entries that sum to $1$.

$$\text{softmax}(t_1, \dots, t_k) = \begin{bmatrix} \frac{\exp(t_1)}{\sum_{j=1}^k \exp(t_j)} \\ \vdots \\ \frac{\exp(t_k)}{\sum_{j=1}^k \exp(t_j)} \end{bmatrix}$$

### Probabilistic Model (Softmax Regression)

Applying the softmax function to the linear scores gives our probabilistic model:
$$\begin{bmatrix} P(y = 1 \mid \mathbf{x}; \mathbf{\theta}) \\ \vdots \\ P(y = k \mid \mathbf{x}; \mathbf{\theta}) \end{bmatrix} = \text{softmax}(t_1, \dots, t_k) = \begin{bmatrix} \frac{\exp(\mathbf{\theta}_1^T \mathbf{x})}{\sum_{j=1}^k \exp(\mathbf{\theta}_j^T \mathbf{x})} \\ \vdots \\ \frac{\exp(\mathbf{\theta}_k^T \mathbf{x})}{\sum_{j=1}^k \exp(\mathbf{\theta}_j^T \mathbf{x})} \end{bmatrix} $$

For notational convenience, we denote the predicted probability for class $i$ as $\phi_i$:
$$P(y = i \mid \mathbf{x}; \mathbf{\theta}) = \phi_i = \frac{\exp(t_i)}{\sum_{j=1}^k \exp(t_j)} = \frac{\exp(\mathbf{\theta}_i^T \mathbf{x})}{\sum_{j=1}^k \exp(\mathbf{\theta}_j^T \mathbf{x})}$$

#### The Negative Log-Likelihood Loss

To find the optimal parameters $\mathbf{\theta} = \{\mathbf{\theta}_1, \dots, \mathbf{\theta}_k\}$, we use **Maximum Likelihood Estimation (MLE)**, which is equivalent to minimizing the **negative log-likelihood** of the training data.

The negative log-likelihood for a single example $(\mathbf{x}, y)$ is:
$$-\log p(y \mid \mathbf{x}, \mathbf{\theta}) = -\log \left( \frac{\exp(t_y)}{\sum_{j=1}^k \exp(t_j)} \right) = -\log \left( \frac{\exp(\mathbf{\theta}_y^\top \mathbf{x})}{\sum_{j=1}^k \exp(\mathbf{\theta}_j^\top \mathbf{x})} \right)$$
The overall **loss function** for the entire training set of $n$ examples is the sum of these negative log-likelihoods, is given as:
$$\ell(\mathbf{\theta}) = \sum_{i=1}^n -\log \left( \frac{\exp(\mathbf{\theta}_{y^{(i)}}^T \mathbf{x}^{(i)})}{\sum_{j=1}^k \exp(\mathbf{\theta}_j^T \mathbf{x}^{(i)})} \right)$$

#### The Cross-Entropy Loss
For simpler notation, it is convenient to define the **cross-entropy loss** $\ell_{\mathrm{ce}} : \mathbb{R}^k \times \{1, \ldots, k\} \rightarrow \mathbb{R}_{\ge 0}$, which modularizes the complex equation above: $$\begin{equation}
\ell_{\mathrm{ce}}((t_1, \ldots, t_k), y) = -\log \left( \frac{\exp(t_y)}{\sum_{j=1}^{k} \exp(t_j)} \right)
\end{equation}$$
With this notation, we can rewrite the **loss function** as
$$\begin{equation}
\ell(\theta) = \sum_{i=1}^{n} \ell_{\mathrm{ce}} \left( (\theta_1^\top x^{(i)}, \ldots, \theta_k^\top x^{(i)}),\, y^{(i)} \right)
\end{equation}$$

> [!tip]  The cross-entropy loss has a simple gradient
> Let $t = (t_1, \ldots, t_k)$ and recall $\phi_i = \frac{\exp(t_i)}{\sum_{j=1}^{k} \exp(t_j)}$
> By basic calculus, we obtain
> $$\begin{equation}
> \frac{\partial \ell_{\mathrm{ce}}(t,y)}{\partial t_i} = \phi_i - \mathbf{1}\{y = i\}
> \end{equation}$$
> where $\mathbf{1}\{\cdot\}$ is the indicator function, i.e., $\mathbf{1}\{y=i\}=1$ if $y=i$, and $0$ otherwise.
> 
> ---
> Alternatively, in vectorized form we have:
> $$\frac{\partial \ell_{\mathrm{ce}}(t,y)}{\partial t} = \phi - e_y$$
> where $e_s \in \mathbb{R}^k$ is the $s$-th standard basis vector (1 in the $s$-th position and zeros elsewhere).

Using the chain rule, we obtain
$$
\frac{\partial \ell_{\mathrm{ce}}((\theta_1^\top x, \ldots, \theta_k^\top x), y)}{\partial \theta_i}
= \frac{\partial \ell(t,y)}{\partial t_i} \cdot \frac{\partial t_i}{\partial \theta_i}
= (\phi_i - \mathbf{1}\{y = i\}) \cdot x$$

Therefore, the gradient of the loss with respect to parameter block $\theta_i$ is
$$\frac{\partial \ell(\theta)}{\partial \theta_i}
= \sum_{j=1}^{n} \left( \phi_i^{(j)} - \mathbf{1}\{y^{(j)} = i\} \right) \cdot x^{(j)}$$
where $\phi_i^{(j)} = \frac{\exp(\theta_i^\top x^{(j)})}{\sum_{s=1}^{k} \exp(\theta_s^\top x^{(j)})}$ is the probability that the model assigns to class $i$ for example $x^{(j)}$.

With these gradients, one can implement (stochastic) gradient descent to minimize the loss function $\ell(\theta)$.

---
## 📐 2.4 Another algorithm for maximizing $\ell(\theta)$: Newton-Raphson method

Returning to **logistic regression** with $g(z)$ being the **sigmoid function**, let's now talk about a different algorithm for maximizing $\ell(\theta)$.

### Newton's method: finding a zero of a function

To get us started, let's consider **Newton's method** for finding a zero of a function. Specifically, suppose we have some function $f: \mathbb{R} \rightarrow \mathbb{R}$, and we wish to find a value of $\theta$ so that $f(\theta) = 0$. Here, $\theta \in \mathbb{R}$ is a real number.

Newton's method performs the following update:
$$\theta := \theta - \frac{f(\theta)}{f'(\theta)}$$

This method has a natural interpretation in which we can think of it as approximating the function $f$ via a **linear function** that is tangent to $f$ at the current guess $\theta$, solving for where that linear function equals to zero, and letting the next guess for $\theta$ be where that linear function is zero.

Here's a gif of the Newton's method in action:
![[Self-Learning/CS229/Images/NewtonIteration_Ani.gif]]

#### Maximizing a Function $\ell(\theta)$ using Newton's method

Newton's method gives a way of getting to $f(\theta) = 0$. 

What if we want to use it to maximize some function $\ell$? The maxima of $\ell$ correspond to points where its **first derivative $\ell'(\theta)$ is zero**. So, by letting $f(\theta) = \ell'(\theta)$, we can use the same algorithm to maximize $\ell$, and we obtain update rule:

$$\theta := \theta - \frac{\ell'(\theta)}{\ell''(\theta)}$$

### Newton-Raphson method: Generalization to Multidimensional $\theta$

Lastly, in our logistic regression setting, $\theta$ is **vector-valued**, so we need to generalize Newton's method to this setting. The generalization of Newton's method to this multidimensional setting (also called the **Newton-Raphson method**) is given by

$$\theta := \theta - H^{-1} \nabla_{\theta}\ell(\theta)$$

Here, $\nabla_{\theta}\ell(\theta)$ is, as usual, the **vector of partial derivatives** of $\ell(\theta)$ with respect to the $\theta_i$'s; and $H$ is an $d \times d$ matrix (actually, $(d+1) \times (d+1)$, assuming that we include the intercept term) called the **Hessian**, whose entries are given by
$$H_{ij} = \frac{\partial^2 \ell(\theta)}{\partial\theta_i \partial\theta_j}$$

Newton's method typically enjoys **faster convergence** than (batch) gradient descent, and requires many fewer iterations to get very close to the minimum. 

One iteration of Newton's can, however, be **more expensive** than one iteration of gradient descent, since it requires finding and inverting an $d \times d$ Hessian; but so long as $d$ is not too large, it is usually much faster overall. 

When Newton's method is applied to maximize the logistic regression log likelihood function $\ell(\theta)$, the resulting method is also called **Fisher scoring**.

---