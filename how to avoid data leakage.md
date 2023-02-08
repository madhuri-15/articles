### Article Link
[Data Leakage in ML](https://medium.com/dev-genius/data-leakage-in-ml-ae19613009ba)


#### Create a synthetic dataset for binary classification.
```python
# Create a dataset
from sklearn.datasets import make_classification
X, y = make_classification(n_samples=2000, n_features=30)

# Shape
print(X.shape, y.shape)
# Output: (2000, 30) (2000,)
```

```python
# Importing required libraries
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score
```

## The wrong approach - spliting data after data preparations.

```python
# Standardization
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Split data into training and test subsets
X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.3, random_state=0)

# Fit the model
knn = KNeighborsClassifier()
knn.fit(X_train, y_train)

# Predict the output
y_preds = knn.predict(X_test)

# Model evaluation
acc = accuracy_score(y_test, y_preds)
print("Accuracy:: %.3f" % (acc*100))
# Output: Accuracy:: 78.333
```

## The right approach - spliting data before any data preparation.
```python
# Split the dataset into train and test datasets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=0)

# Define scaler
scaler = StandardScaler()

# Fit transformation on train subset
scaler.fit(X_train)

# Apply transfromation on training dataset
X_train = scaler.transform(X_train)

# Apply transfromation on test dataset
X_test = scaler.transform(X_test)

# Fit the model
knn = KNeighborsClassifier()
knn.fit(X_train, y_train)

# Predict the output
y_preds = knn.predict(X_test)

# Model evaluation
acc = accuracy_score(y_test, y_preds)
print(“Accuracy:: %.3f” % (acc*100))
# Output: Accuracy:: 76.667
```
### Using pipeline
```python
# Using pipeline
from sklearn.pipeline import make_pipeline

# Split the dataset into train and test datasets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=0)

# Make pipeline
pipeline = make_pipeline(StandardScaler(), KNeighborsClassifier())

# fit the model
pipeline.fit(X_train, y_train)
y_preds = pipeline.predict(X_test)

# Model evaluation
acc = accuracy_score(y_test, y_preds)
print(“Accuracy:: %.3f” % (acc*100))
# Output: Accuracy:: 76.667
```
### Using K-fold cross validation

```python
# Using cross-val-score
from sklearn.model_selection import cross_val_score

# Model evaluation using cross-validation
scores = cross_val_score(pipeline, X, y)
print(“Accuracy:: %.3f” % (scores.mean()*100))
# Output: Accuracy:: 71.500

```
