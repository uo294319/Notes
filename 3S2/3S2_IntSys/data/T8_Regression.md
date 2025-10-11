# Linear Regression
---
[Go Back](../README.md)

---
## Definition

> **Linear regression** is a supervised machine learning algorithm that models the linear relationship between a dependent variable (target or output) and one or more independent variables (features or inputs).

## Mathematical definition
### 1. Objective
Given a set of features $x_1$, $x_2$, ... $x_d$ we want to be able to predict the target $y$.

$$h:x\mapsto y$$

- We know some $x$ and $y$  in order to establish a linear relation called Dataset ($D$).
### 2. Linear Regression Function
We define the linear function $h_\theta(x)$
Try to find a set of parameters (called weights) $\theta_0$, $\theta_1$, ... $\theta_n$ so that $h(x)$ is close to $y$

$$h_\theta(x) = \theta_0 + \theta_1 x_1 + ... + \theta_d x_n$$

For simplicity we consider $x_0 = 1$ (intercept term):

$$h_\theta(x) = \sum_{i=0}^n \theta_i x_i$$

Or in a vectorial expression: $h_\theta(x) = \theta^Tx$
### 3. Cost Function
- We define a cost function $J(\theta)$.
- $J(\theta)$ tells us how apart is $h_\theta(x)$ (prediction) from $y$ (real value) based on the weights.
- The objective is to minimise $J(\theta)$ or $\theta \leftarrow \arg\min_\theta J(\theta)$.
- The process of minimising the cost is called training.

$$J(\theta) = \frac{1}{|D|}\sum_{(x, y)\in D}loss(y, h_\theta(x))$$

There are many but we use the least-squares.

$$J(\theta) = \frac{1}{2}\sum_{i=1}^n(h_\theta(x_i) - y_i)^2$$

- To do so we can use the gradient descent algorithm.
### 4. Gradient Descent
- Algorithm to obtain the weights $\theta$ that minimices the cost function $J(\theta)$.
- It is based on minimising the first-order Taylor Polynomial approximation for $h$.

$$
\begin{equation}\begin{split}
&\theta := \theta_0 \\
&\text{repeat} \\
&\quad\theta := \theta - \gamma\times \frac{
\partial}{\partial \theta}J(\theta)\\
&\text{until we reach a minimun} \\
&\text{return}\:\theta
\end{split}\end{equation}
$$

- The $\theta_0$ is chosen at random.
- Loop update
	- Must be simultaneous to all $\theta$
	- Grants a local minimum but not an absolute one.
	- As $h(x)$ is linear:
		- $J$ is a convex quadratic function.
		- There will only be 1 minimum, so we approximate to the absolute minimum.
- Learning rate
	- How much we adjust $\theta$ each update.
	- Small cause the algorithm to converge slow.
	- But too large may cause the algorithm to diverge.
- Derivative parte
	- Stochastic Gradient Descent with mini batch
		- Derivative part is difficult to calculate.
		- We estimate the average with the subset $D'$.

If we do the derivative:
$$
\begin{equation}\begin{split}
&\theta_j := \theta_j - \alpha\times \frac{
\partial}{\partial \theta_j}J(\theta)\\
&\theta_j := \theta_j - \alpha\times \frac{
\partial}{\partial \theta_j}\frac{1}{2}(h_\theta(x) - y)^2\\
&\theta_j := \theta_j - \alpha\times (h_\theta(x) - y) \times\frac{
\partial}{\partial \theta_j}(h_\theta(x) - y)\\
&\theta_j := \theta_j - \alpha\times (h_\theta(x) - y) \times x_j\\
\end{split}\end{equation}
$$

- This means that as we approximate the minimum, the update minimises.
- This is called Least Mean Squares (LMS)
---