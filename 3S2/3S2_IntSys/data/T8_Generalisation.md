# Generalisation and regularisation
---
[Go Back](../README.md)

---
## Generalization
- Model ability to perform well under new data.
- Objective is to minimize test error not training erro.
- If we only try to minimise training error we may have overfitting
## Bias-Variance Tradeoff
- **Bias**
	- Error due to simplistic assumptions
	- Model is too simple and underfits the data.
- **Variance**
	- Error due to over-sensitivity
	- Model is too complex and overfits the training data.
	- we try to find a optimal tradeoff. A balance where test error is minimized.
## Regularization
 - Technique to **control** model complexity and prevent overfitting.
 - Adds a penalty term (regularizer) to the loss function to restrict extreme parameter values
 - Usually the norms 1 and 2 are used for linear models and norm-2 for deep-learning.