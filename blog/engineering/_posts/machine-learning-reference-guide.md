# Data Processing

## Log-transform the skewed features
A dataset may sometimes contain at least one feature whose values tend to lie near a single number, but will also have a
non-trivial number of vastly larger or smaller values than that single number. Algorithms can be sensitive to such 
distributions of values and can underperform if the range is not properly normalized.    
Using a logarithmic transformation significantly reduces the range of values caused by outliers.
```python
skewed = ['<feature_column_name_1>', '<feature_column_name_2>']
features_log_transformed = pd.DataFrame(data = features_raw)
# log(x + 1) to avoid log(0) which is undefined
features_log_transformed[skewed] = features_raw[skewed].apply(lambda x: np.log(x + 1))
```

## One-hot Encoding
Typically, learning algorithms expect input to be numeric, which requires that non-numeric features (called categorical
variables) be converted. One popular way to convert categorical variables is by using the one-hot encoding scheme. 
One-hot encoding creates a "dummy" variable for each possible category of each non-numeric feature. For example, 
assume someFeature has three possible entries: A, B, or C. We then encode this feature into someFeature_A, someFeature_B
and someFeature_C.
```python
features_final = pd.get_dummies(features_original)
```

## Manual Encoding
If a column/feature has only two possible categories, we can avoid using one-hot encoding and simply encode these two
categories as 0 and 1, respectively.
```python
income = income_raw.replace(['<=50K', '>50K'], [0, 1])
```

## Scikit - Feature Scaling
Normalisation/Scaling ensures that each feature is treated equally when applying supervised learners.
```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler() # default=(0, 1)
numerical = ['age', 'education-num', 'capital-gain', 'capital-loss', 'hours-per-week']

features_log_minmax_transform = pd.DataFrame(data = features_log_transformed)
features_log_minmax_transform[numerical] = scaler.fit_transform(features_log_transformed[numerical])
```

## Split Data - Training and Testing
```python
from sklearn.model_selection import train_test_split

# Split the 'features' and 'income' data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X_raw, 
                                                    y_raw, 
                                                    test_size = 0.2, 
                                                    random_state = 0)
```