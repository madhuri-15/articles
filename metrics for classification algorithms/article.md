### Article Link
[Classification metrics for more promising model performance](https://medium.com/dev-genius/classification-metrics-5713f5a7b8e5)

### Code 
```python
## Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
sns.set_style("whitegrid")

from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

## read data
data = pd.read_csv("data.csv")
X = data.drop(['loan_default'], axis=1)
y = data['loan_default']

## distribution
print("Y distribution:\n", y.value_counts())

## split the data into 70% of training data and 30% of test data.
X_train, X_test, y_train, y_test = train_test_split(X, y,
                                                    train_size=0.7,
                                                    random_state=1)
## Train algorithm
clf = RandomForestClassifier(random_state=1)
## fit the data
clf.fit(X_train, y_train)
## Predict the output
y_predicts = clf.predict(X_test)

## Ouput:
## Y distribution: 
## 0    4200
## 1    2800
```
- Confusion Matrix
```python
## Confusion matrix
from sklearn.metrics import confusion_matrix
from sklearn.metrics import ConfusionMatrixDisplay
cm = confusion_matrix(y_test, y_predicts)
disp = ConfusionMatrixDisplay(confusion_matrix=cm, 
                              display_labels=clf.classes_)
disp.plot()
plt.show()
```
- Accuracy
```python
## Accuracy score.
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, y_predict)
print("Accuracy Score: %.3f" %(accuracy))
# Output: Accuracy Score: 0.579
```

- Precision
```python
# precision score
from sklearn.metrics import precision_score
precision = precision_score(y_test, y_predict)
print("Precision Score: %.3f" %(precision))
# Output: Precision Score: 0.450
```

- Recall or Sensitivity (True Positive Rate)
```python
# recall score
from sklearn.metrics import recall_score
recall = recall_score(y_test, y_predict)
print("Recall Score: %.3f" %(recall))
# Output: Recall Score: 0.320
```

- F1-Score
```python
# f1-score
from sklearn.metrics import f1_score
score = f1_score(y_test, y_predict, average='macro')
print("F1 Score: %.3f" %(score))
# Output: F1 Score: 0.528
```

- ROC Curve

```python
# ROC Curve
from sklearn.metrics import RocCurveDisplay
RocCurveDisplay.from_estimator(clf, X, y)
plt.plot([0, 1], linestyle="--", color='black')
plt.show()
```
