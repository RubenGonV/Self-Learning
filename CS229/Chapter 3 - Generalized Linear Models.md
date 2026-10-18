---
First Created: "{{today}}"
tags:
  - CS229
---
```table-of-contents
maxLevel:2
```

---
# Chapter 3 - Generalized Linear Models (GLMs)

So far, we've looked at two distinct examples: a **regression** example and a **classification** example.

1. **Regression Example:** Here, we modeled the continuous outcome as following a Gaussian distribution. $y \ | \ x; \theta \sim \mathcal{N}(\mu, \sigma^2)$, where the conditional mean $\mu$ is some function of the features $x$ and parameters $\theta$.

2. **Classification Example:** Here, we modeled the binary outcome as following a Bernoulli distribution. $y \ | \ x; \theta \sim \text{Bernoulli}(\phi)$, where the probability of success $\phi$ is some function of the features $x$ and parameters $\theta$.

We will now show that both of these methods are **special cases of a broader family of models** called **Generalized Linear Models (GLMs)**.

We will also demonstrate how other models within the GLM family can be derived and applied to solve different types of classification and regression problems.

![[Exponential Family of Distributions by Bruno Magalhaes.png]]
## 📈 3.1 The exponential family

To work our way up to **GLMs**, we will begin by defining **exponential family distributions**. 

We say that a class of distributions is in the exponential family if it can be written in the form:$p(y; \eta) = b(y) \exp(\eta^T T(y) - a(\eta))$.

![[Pasted image 20251209184108.png]]
Here:
- **$\eta$** is called the **natural parameter** (also called the **canonical parameter**) of the distribution.
- **$T(y)$** is the **sufficient statistic** (for the distributions we consider, it will often be the case that $T(y) = y$).
- **$a(\eta)$** is the **log partition function**. 
 
The quantity $e^{-a(\eta)}$ essentially plays the role of a normalization constant, that makes sure the distribution $p(y; \eta)$ sums/integrates over $y$ to 1.

> A fixed choice of $T$, $a$, and $b$ defines a *family* (or set) of distributions that is parameterized by $\eta$ ; as we vary $\eta$, we then get different distributions within this family.

---

We now show that the **Bernoulli** and the **Gaussian** distributions are examples of exponential family distributions.

### 1. The Bernoulli Distribution

The Bernoulli distribution with mean $\phi$, written $\text{Bernoulli}(\phi)$, specifies a distribution over $y \in \{0, 1\}$, so that $p(y = 1; \phi) = \phi$ and $p(y = 0; \phi) = 1 - \phi$. As we vary $\phi$, we obtain Bernoulli distributions with different means. We now show that this class of Bernoulli distributions is in the exponential family.

We write the Bernoulli distribution as:
$$p(y; \phi) = \phi^y (1 - \phi)^{1-y}$$

We can rewrite this using the exponential function:
$$\begin{aligned} p(y; \phi) &= \exp(\log(\phi^y (1 - \phi)^{1-y})) \\ &= \exp(y \log \phi + (1 - y) \log(1 - \phi)) \\ &= \exp \left( \left( \log \left( \frac{\phi}{1 - \phi} \right) \right) y + \log(1 - \phi) \right) \end{aligned}$$

Comparing this to the exponential family form $p(y; \eta) = b(y) \exp(\eta^T T(y) - a(\eta))$, we have:

- **Natural Parameter**: $\eta = \log ( \phi / (1 - \phi) )$

Interestingly, by solving for $\phi$ in terms of $\eta$, we obtain $\phi=1/(1+e^{-\eta})$. This is the familiar sigmoid function! This will come up again when we derive logistic regression as a GLM.

We also have:
- $T(y) = y$
- $a(\eta) = - \log(1 - \phi) = log(1+e^\eta)$ 
- $b(y) = 1$

This shows that the Bernoulli distribution can be written in the form of Equation (3.1).

---
### 2. The Gaussian (Normal) Distribution

Let’s now move on to consider the Gaussian distribution.

Recall that, when deriving linear regression, the value of $\sigma^2$ had no effect on the final choice of $\theta$. To simplify the derivation, we set $\sigma^2 = 1$. The probability density function is:
$$p(y; \mu) = \frac{1}{\sqrt{2\pi}} \exp \left( - \frac{1}{2} (y - \mu)^2 \right)$$

We can rewrite this as:
$$\begin{aligned} p(y; \mu) &= \frac{1}{\sqrt{2\pi}} \exp \left( - \frac{1}{2} (y^2 - 2 \mu y + \mu^2) \right) \\ &= \frac{1}{\sqrt{2\pi}} \exp \left( - \frac{1}{2} y^2 \right) \cdot \exp \left( \mu y - \frac{1}{2} \mu^2 \right) \end{aligned}$$

Thus, we see that the Gaussian (with $\sigma^2=1$) is in the exponential family, with:
- $\eta = \mu$
- $T(y) = y$
- $a(\eta) = \frac{\mu^2}{2} = \frac{\eta^2}{2}$
- $b(y) = \frac{1}{\sqrt{2\pi}} \exp \left( - \frac{1}{2} y^2 \right)$

### Other Members of the Exponential Family

There are many other distributions that are members of the exponential family, including:

- The **Multinomial**
- The **Poisson** (for modelling count-data)
- The **Gamma** and the **Exponential** (for continuous, non-negative random variables)
- The **Beta** and the **Dirichlet** (for distributions over probabilities)

In the next section, we will describe a general "recipe" for constructing models, known as GLMs, in which the response variable $y$ (given $x$ and $\theta$) comes from any of these distributions.

---

## 🛠️3.2 Constructing GLMs

To derive a **GLM** for predicting the value of a random variable $y$ as a function of $x$, we rely on the following three assumptions/design choices about the conditional distribution of $y$ given $x$:

1. **Exponential Family Distribution:** Given $x$ and $\theta$, the distribution of $y$ follows some exponential family distribution: $y \ |\  x; \theta \sim \text{ExponentialFamily}(\eta)$, with parameter $\eta$.

2. **The goal is to Predict Expected Value:** Our prediction $h(x)$ aims to satisfy the expected value of the sufficient statistic $T(y)$ given $x$. In most cases, where $T(y) = y$, the goal is:
$$h(x) = E[y|x]$$
	(This is satisfied by both linear regression and logistic regression, e.g., for logistic (Bernoulli), we had $h_\theta(x) = p(y=1|x;\theta) = 0 \cdot p(y = 0|x; \theta) + 1 \cdot p(y = 1|x; \theta) = E[y|x; \theta]$.)

3. **Linear Relationship:** The natural parameter $\eta$ is linearly related to the inputs $x$:
$$\eta = \theta^T x$$

These three assumptions/design choices will allow us to derive a very elegant class of learning algorithms, namely GLMs, that have many desirable properties such as **ease of learning**. 

---
### 3.2.1 Ordinary Least Squares (OLS) as a GLM

To show that **Ordinary Least Squares** is a special case of the GLM, we assume the response variable $y$ is continuous and the conditional distribution $y \mid x$ is a **Gaussian** $\mathcal{N}(\mu, \sigma^2)$.

1. **Distribution:** $y \mid x; \theta \sim \mathcal{N}(\mu, \sigma^2)$.
2. **Canonical Property:** For the Gaussian, the mean $\mu = \eta$ the natural parameter.

Applying the GLM assumptions:
$$\begin{aligned} h_\theta(x) &= E[y\mid x; \theta] \quad &\text{(Assumption 2)} \\ &= \mu \quad &\text{(Expected value of Gaussian)} \\ &= \eta \quad &\text{(Canonical Property)} \\ &= \theta^T x \quad &\text{(Assumption 3)} \end{aligned}$$

This results in the linear hypothesis function: $h_\theta(x) = \theta^T x$.

---
### 3.2.2 Logistic Regression

For **binary classification**, where $y \in \{0, 1\}$, we choose the **Bernoulli family** of distributions to model $y \mid x$.

1. **Distribution:** $y \mid x; \theta \sim \text{Bernoulli}(\phi)$.
2. **Canonical Property:** For the Bernoulli, the relationship between the mean ($\phi$) and the natural parameter ($\eta$) is $\phi = 1/(1 + e^{-\eta})$. Also, $E[y\mid x; \theta] = \phi$.

Applying the GLM assumptions:
$$\begin{aligned} h_\theta(x) &= E[y\mid x; \theta] \quad &\text{(Assumption 2)} \\ &= \phi \quad &\text{(Expected value of Bernoulli)} \\ &= 1/(1 + e^{-\eta}) \quad &\text{(Canonical Property)} \\ &= 1/(1 + e^{-\theta^T x}) \quad &\text{(Assumption 3: $\eta = \theta^T x$)} \end{aligned}$$

This is why **Logistic Regression** uses the hypothesis function $h_\theta(x) = 1/(1 + e^{-\theta^T x})$.


> [!info] Extra terminology
> To introduce a little more terminology, the function $g$ giving the distribution's mean as a function of the natural parameter ($g(\eta) = E[T(y); \eta]$) is called the **canonical response function**. Its inverse, $g^{-1}$, is called the **canonical link function**. 
> 
> Thus, the canonical response function for the Gaussian family is just the identity function; and the canonical response function for the Bernoulli is the logistic function.

---