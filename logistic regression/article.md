### Article link
[ML Algorithm: Logistic Regression for a Base Model](https://medium.com/mlearning-ai/ml-algorithm-logistic-regression-for-a-base-model-35ca5f5029e4)

### Code

```python
# Importing libraries
import pandas as pd
import numpy as np

from sklearn.model_selection import train_test_split
from sklearn.feature_extraction import DictVectorizer
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import roc_auc_score

# Load the data
df = pd.read_csv("data.csv")

# Split the data
df_train, df_test = train_test_split(df, test_size=0.3, random_state=1)

# shape
print("Training shape:: ", df_train.shape)
print("Testing shape:: ", df_test.shape)
## Ouput
Training shape:: (4930, 21)
Testing shape:: (2113, 21)

# create y_train and y_test
y_train = df_train['churn']
y_test = df_test['churn']

# delete `churn` attribute from data
del df_train['churn']
del df_test['churn']
train_dict = df_train.to_dict(orient='records')
test_dict = df_test.to_dict(orient='records')

# Data transformation
dv = DictVectorizer(sparse=False)
X_train = dv.fit_transform(train_dict)
X_test = dv.transform(test_dict)

# Train the model
clf = LogisticRegression(max_iter=1000, solver='liblinear')
clf.fit(X_train, y_train)

# Prediction
y_preds = clf.predict_proba(X_train)
print(y_preds[0])
## Output - [0.8218741 0.1781259]

# Model evaluation
y_preds = clf.predict_proba(X_train)[:, 1]
auc = roc_auc_score(y_train, y_preds)
print("Train score:: %.3f" % auc)

y_preds = clf.predict_proba(X_test)[:, 1]
auc = roc_auc_score(y_test, y_preds)
print("Test score:: %.3f" % auc)
## Output - 
Train score:: 0.845
Test score:: 0.858
```
