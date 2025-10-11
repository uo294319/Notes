# DL Classification
---
[Go Back](../README.md)

---
## Analysing data
Professor provides the function `plot_decision_boundary` defined as follows:
```python
# Function to visualize data and model decision boundary
def plot_decision_boundary(X_train, Y_train, X_test, Y_test, model, model_name):
    plt.figure(figsize = (8, 6))

    # Create a mesh grid of points within the range of Train and Test data
    x_min, x_max = min(X_train[:, 0].min(), X_test[:, 0].min()) - 0.5, max(X_train[:, 0].max(), X_test[:, 0].max()) + 0.5
    y_min, y_max = min(X_train[:, 1].min(), X_test[:, 1].min()) - 0.5, max(X_train[:, 1].max(), X_test[:, 1].max()) + 0.5
    xx, yy = np.meshgrid(np.linspace(x_min, x_max, 100), np.linspace(y_min, y_max, 100))

    # Predict the probability for each point in the mesh
    grid = np.c_[xx.ravel(), yy.ravel()]
    Z = model.predict(grid).reshape(xx.shape)

    # Draw the decision boundary
    contour = plt.contourf(xx, yy, Z, levels = [0, 0.5, 1], alpha = 0.7, cmap = 'coolwarm')

    # Add colorbar
    plt.colorbar(contour)

    # Visualize the Train points
    plt.scatter(X_train[:, 0], X_train[:, 1], c = Y_train, cmap = 'coolwarm', edgecolors = 'k', label = 'Train Data')
    
    # Visualize the Test points
    plt.scatter(X_test[:, 0], X_test[:, 1], c = Y_test, cmap = 'coolwarm', marker = 'X', label = 'Test Data')

    # Labels and legend
    plt.xlabel('Sector1Time')
    plt.ylabel('Sector1Time')
    plt.title(f'Decision Boundary: {model_name}')
    plt.legend()
    plt.show()

plot_decision_boundary(X_train, Y_train, X_test, Y_test, baseline_random, 'Baseline Random')
```
---
## Data preprocessing
### Multi-classification Problems
Transforms categorical values to several columns with `1` or `0` in them. Only one `1` per row.
```python
data = pd.get_dummies(data, dtype=int)
```
![[../assets/pd_dummies.png]]
### Multi-label Problems
Same as below but it can have several labels (multiple `1` per row).
```python
mlb = MultiLabelBinarizer()

dummies = pd.DataFrame(mlb.fit_transform(data['Col']), columns = map(lambda x: 'Dummie_'+str(x), mlb.classes_))
```
---
## Neural Networks
### 1 - Imports and model creation
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Input

model = Sequential()
```
### 2 - Add layers
- Each layer of neurons can have activation functions
	![[../assets/func.png]]
	- `sigmoid` is used in the output layer for classification problems.
		- Only one that produces a number between 0 and 1 (a probability).
	- `tahn` is often used in the hidden layers when negative values help.
	- `relu` is often used in the hidden layers with no negative values.
```python
# Add the input layer (where the shape is the # of input values)
model.add(Input(shape=(1, ))) # X_train.shape[1]

# Add more layers of neurons
model.add(Dense(32, activation='tanh', name = 'hidden_layer_1'))
model.add(Dense(16, activation='tanh', name = 'hidden_layer_2'))
#...

# Add the output layer (where the shape is the # of outpu values)
model.add(Dense(1, name = 'output_layer')) # Y_train.shape[1]
```
### 3 - Choose an optimiser
Defines how the model will adjust its weights)
- Low learning rate can result in slow learning
- High learning rate can result in over-fitting to the train data 
```python
optim = Adam(learning_rate = 0.001)
```
### 4 - Compile the model
We should choose the loss to minimise:
- `categorical_crossentropy` for multi-class classification.
- `binary_crossentropy` for binary or multi-label classification.
- `mean_squared_error` or `mean_absolute_error` for regression.
```python
model.compile(loss = 'mean_absolute_error', optimizer = optim)
```
### 5 - Train the model
- The model reserves the P percentage of the data for validation where P is `validation_split`.
	- Technique that splits data into Train, Validation, and Test sets is called meta-validation.
	- Helps monitor over-fitting and adjust hyper-parameters.
- The model updates its weights after seeing N samples where N is the `batch_size`.
- The model loops over the entire training data N times where N is the `epochs`.
```python
history = model.fit(X_train, Y_train, validation_split = 0.2, batch_size = 64, epochs = 200, verbose = 2)
```
### 6 - Visualise training and validation losses
Professor provides the function `plot_loss_history(history)` defined as follows:
```python
def plot_loss_history(history):
    # Extract the history data
    loss = history.history['loss']
    val_loss = history.history.get('val_loss', None)  # It may not exist if validation was not used
    epochs = range(1, len(loss) + 1)

    # Create a DataFrame for seaborn
    data = pd.DataFrame({ 'Epoch': list(epochs) * 2, 'Loss': loss + (val_loss if val_loss else []), 'Type': ['Train'] * len(loss) + (['Validation'] * len(val_loss) if val_loss else []) })

    # Create the plot
    plt.figure(figsize = (10, 5))
    sns.lineplot(data = data, x = 'Epoch', y = 'Loss', hue = 'Type')
    plt.xlabel('Epochs')
    plt.ylabel('Loss')
    plt.title('Loss Evolution during Training')
    plt.legend(title = 'Set')
    plt.grid(True)
    plt.show()

# Call the function (after training the model)
plot_loss_history(history)
```
---
## Summary
| Problem Type              | Activation function in the output layer | Loss function                              |
| ------------------------- | --------------------------------------- | ------------------------------------------ |
| Regression                | None or *ReLU* (if values are positive) | `mean_absolute_error` `mean_squared_error` |
| Binary Classification     | Sigmoid                                 | `binary_crossentropy`                      |
| Multiclass Classification | Softmax                                 | `categorical_crossentropy`                 |
