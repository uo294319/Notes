# Classification
---
[Go Back](../README.md)

---
## Logistic Regression
- We try to have $h:x\mapsto y$  where $y \in \{0, 1\}$.
	- We will use the logistic function or sigmoid $g(z) = \frac{1}{1+\exp(-z)}$
	- So we use $h_\theta = g(\theta^T x)$ being $\theta$ the weights.
- We find the best $\theta$ by maximum likelihood.
	- We try to maximise the the likelihood of observing the actual data under the model.
	- This means maximising $\log L(\theta) = \log \prod P(y^{(i)}|x^{(i)}, \theta)$
	- We minimize the cost function (cross entropy) with gradient descent.
		- At the end same expression as linear regression but with new $h_\theta(x)$
- Conclusion
	- Builds an hypothesis that estimates the probability that an entry $x$ belongs to a class.
- Separation rule
	- We define a threshold.
	- If $h_\theta(x)$ is greater than the threshold we assume $y = 1$, otherwise we assume $y = 0$.
- Multi-class Classification
	- We produce a set of $k$ outputs that are a multinomial distribution.
		- Each output is the probability for that class.
		- Sum of outputs is $1$.
	- We use softmax function.
---
## Generative Learning
- We want to distinguish between different classes.
	- In logistic regression we model $p(y|x)$
	- Now we want to model $p(x|y)$
	- Use Bayes rule $p(y|x) = \frac{p(x|y)\times p(y)}{p(x)}$
	- Gaussian Discriminant Analysis (GDA) performs better than logistic regression.
- Naive Bayes
	- With a set of inputs $x$
	- We make predictions $p(y | x) = p(x|y)\times p(y) = \prod p(x_i|y)\times p(y)$
---