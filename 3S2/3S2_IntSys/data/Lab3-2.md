# ML Regression
---
[Go Back](../README.md)

---
## Baseline Model
```python
# Typically the mean is used
baseline_media = sk.dummy.DummyRegressor(strategy="mean")
baseline_media.fit(X_train, Y_train)

Y_pred = baseline_media.predict(X_train)
```
---
## Regression Models
### Linear Regression
```python
model_linear = sk.linear_model.LinearRegression()
model_linear.fit(X_train, Y_train)

Y_pred = model_linear.predict(X_train)
```
### Polynomial Regression
```python
# Transform the features into polynomial features
poly = sk.preprocessing.PolynomialFeatures(degree = 3) 
X_train_poly = poly.fit_transform(X_train)
X_test_poly = poly.transform(X_test)

# Fit the linear regression model to the polynomial features
model_poly = sk.linear_model.LinearRegression()
Y_pred = model_poly.fit(X_train_poly, Y_train)
```
### Other
```python
# Choose one
model = sk.neighbors.KNeighborsRegressor()
model = sk.tree.DecisionTreeRegressor()
model = sk.svm.SVR()

# Then
model.fit(X_train, Y_train)
Y_pred = model.predict(X_train)
```
---
## Model Evaluation
### Visualisation
```python
plt.figure(figsize = (12,8))

sns.scatterplot(x = X_train.flatten(), y = Y_train, label = 'Train data')
sns.scatterplot(x = X_test.flatten() , y = Y_test , label = 'Test data' )

# ... (Model prediction)

X_range = [i/10 for i in range(-10, 41)]
plot = sns.lineplot(x = X_range, y = Y_pred, label = 'Regression')

plot.set_xlabel('X')
plot.set_ylabel('Y')
plot.set_title('Title X-Y')
plt.show()
```
### Errors
```python
print("MAE", sk.metrics.mean_absolute_error(Y_test, Y_pred))
print("MSE", sk.metrics.mean_squared_error(Y_test, Y_pred))
print("R^2", sk.metrics.r2_score(Y_test, Y_pred))
```
---