
# 📝 Machine Learning Notation

To establish notation for future use, we'll use $\mathbf{x}^{(i)}$ to denote the **"input variables"** (living area in this example), also called **input features**, and $\mathbf{y}^{(i)}$ to denote the **"output"** or **target variable** that we are trying to predict (price).

A pair $(\mathbf{x}^{(i)}, \mathbf{y}^{(i)})$ is called a training example, and the dataset that we'll be using to learn—a list of $n$ training examples

$$\{(\mathbf{x}^{(i)}, \mathbf{y}^{(i)}); i = 1, \dots, n\}$$

—is called a training set.

Note that the superscript $(i)$ in the notation is simply an **index** into the training set, and has nothing to do with exponentiation.

We will also use $\mathcal{X}$ denote the space of input values, and $\mathcal{Y}$ the space of output values. In this example, $\mathcal{X} = \mathcal{Y} = \mathbb{R}$.

To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function $h : \mathcal{X} \mapsto \mathcal{Y}$ so that $h(x)$ is a “good” predictor for the corresponding value of $y$. For historical reasons, this function $h$ is called a **hypothesis**.

When the target variable that we’re trying to predict is continuous, such as in our housing example, we call the learning problem a **regression** problem. When y can take on only a small number of discrete values (such as if, given the living area, we wanted to predict if a dwelling is a house or an apartment, say), we call it a **classification** problem.
