# Ensemble learning
---
[Go Back](../README.md)

---
## Ensemble Methods
- Is a method to improve performance of weak learners.
- Wisdom of the crowd.
	- Instead of using an only weak learner (classification trees)
		- Use several ones to create a strong learner. (bagging)
		- We aggregate them to ensure lower variance.
	- To ensure different outcomes we get different subsets of the data
	- Choose the majority voting class or the average of results.
- Random forest
	- Same expectations and bias of individual trees.
	- Is a bag of trees identically distributed. (correlated)
	- Decorrelation. Each bag uses only a random subset of features
		- For the full features $m$ we only use $k$.
			- $k=m$ same as bagging
			- $k < m$ random forest
		- $k$ works as a hyperparameter.
	- Problem when only a few features are relevant.
---