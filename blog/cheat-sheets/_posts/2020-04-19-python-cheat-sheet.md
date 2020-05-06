---
layout: post
title:  "Python cheat sheet"
teaser: Python Cheat Sheet - Pandas, Numpy, Anaconda, Jupyter
date:   2020-04-19 00:00:00 +0000
categories: cheat-sheets
tags: cheat-sheets
permalink: /blog/python-cheat-sheet
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Pandas](#pandas)
  - [Read CSV as a DataFrame](#read-csv-as-a-dataframe)
  - [Get Column by Label](#get-column-by-label)
  - [Get All Rows Where Column Value Satisfies Condition](#get-all-rows-where-column-value-satisfies-condition)
  - [Get Column by Index](#get-column-by-index)
  - [Get Row by Label](#get-row-by-label)
  - [Get Row by Index](#get-row-by-index)
  - [Drop a column from DF](#drop-a-column-from-df)
  - [Append Columns from a DF to another DF](#append-columns-from-a-df-to-another-df)
  - [Transform Values of Selected Columns of a DF](#transform-values-of-selected-columns-of-a-df)
  - [Replace Values in Columns of a DF](#replace-values-in-columns-of-a-df)
  - [Sum of a Panda Series Using Numpy](#sum-of-a-panda-series-using-numpy)
  - [Count of Number of Elements in a Pandas Series](#count-of-number-of-elements-in-a-pandas-series)
  - [Get N Rows from a DF](#get-n-rows-from-a-df)
  - [Get N Random Rows from a DF](#get-n-random-rows-from-a-df)
- [Data Visualisation](#data-visualisation)
  - [Draw Distribution of a Column Value](#draw-distribution-of-a-column-value)
- [Anaconda](#anaconda)
  - [Update all packages](#update-all-packages)
  - [Install package](#install-package)
  - [Remove package](#remove-package)
  - [Search package](#search-package)
  - [List packages](#list-packages)
- [Jupyter](#jupyter)
  - [Convert notebook to html](#convert-notebook-to-html)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Pandas

## Read CSV as a DataFrame
```python
data = pd.read_csv("census.csv")
```

## Create DF manually
```python
df = pd.DataFrame([[1, 2], [4, 5], [7, 8]],
         index=['cobra', 'viper', 'sidewinder'],
         columns=['max_speed', 'shield'])
```

## Get Column by Label
```python
df.shape                    # rows x columns

# Option 1
df[['column_label']]

# Option 2
df.loc[:, ['column_label']]       

df[['column_label']].shape  # rows x 1
```

## Get All Rows Where Column Value Satisfies Condition
```python
df.loc[df['column_label'] > 4]
```

## Get Column by Index
```python
df.shape                    # rows x columns
df.iloc[:, [0]]
df.iloc[:, [0]].shape       # rows x 1
```

## Get Row by Label
```python
df.shape                    # rows x columns
df.loc[['row_label']]
df.loc[['row_label']].shape # 1 x columns
```

## Get Row by Index
```python
df.shape                    # rows x columns
df.iloc[[0]]
df.loc[[0]].shape           # 1 x columns
```

## Drop a column from DF
```python
features_raw = data.drop('<column_name>', axis = 1) # axis = 1 => axis = 'columns'
```

## Append Columns from a DF to another DF
```python
df1.join(df2)
```

## Transform Values of Selected Columns of a DF
```python
columns_to_transform = ['<feature_column_name_1>', '<feature_column_name_2>']
features_log_transformed = pd.DataFrame(data = features_raw)
features_log_transformed[skewed] = features_raw[columns_to_transform].apply(lambda x: np.log(x + 1))
```

## Replace Values in Columns of a DF
```python
# Replace value a with 0 and b with 1
data = data_raw.replace(['a', 'b'], [0, 1])
```

## Sum of a Panda Series Using Numpy
```python
np.sum(a_series)
```

## Count of Number of Elements in a Pandas Series
```python
a_series.count()
```

## Get N Rows from a DF
```python
df[:n]
```

## Get N Random Rows from a DF
```python
df.sample(n=N)
```

# Sample Data
```python
import numpy as np
import pandas as pd

# Load the Census dataset
census_df = pd.read_csv("census.csv")

# Success - Display the first record
display(census_df.head(n=10))

from sklearn.datasets import load_boston
from sklearn.datasets import load_diabetes

# https://scikit-learn.org/stable/datasets/index.html#boston-dataset
dataset = load_boston()

# dataset_2 = load_diabetes()

# print(np.append(dataset['feature_names'], 'bla'))
# print(type(dataset['feature_names']))
# print(dataset_2['feature_names'] + ['bla'])
# print(type(dataset_2['feature_names']))

dataset_df = pd.DataFrame(
    data=np.column_stack((dataset['data'], dataset['target'])), 
    columns=(np.append(dataset['feature_names'], 'MEDV'))
)

display(dataset_df.head())

data = census_df
```

# Data Visualisation
```
## Sample Data
  	age	workclass	education_level	education-num	marital-status	occupation	relationship	race	sex	capital-gain	capital-loss	hours-per-week	native-country	income
0	39	State-gov	Bachelors	13.0	Never-married	Adm-clerical	Not-in-family	White	Male	2174.0	0.0	40.0	United-States	<=50K
1	50	Self-emp-not-inc	Bachelors	13.0	Married-civ-spouse	Exec-managerial	Husband	White	Male	0.0	0.0	13.0	United-States	<=50K
2	38	Private	HS-grad	9.0	Divorced	Handlers-cleaners	Not-in-family	White	Male	0.0	0.0	40.0	United-States	<=50K
```

## Plot Distribution of a Column Value Where Column_2 Value Satisfies Condition
```python
import seaborn as sns

%matplotlib inline
sns.set(style="ticks")

target_0 = data.loc[data['income'] == '>50K']
target_1 = data.loc[data['income'] == '<=50K']

sns.distplot(target_0[['age']])
sns.distplot(target_1[['age']])
```

## Plot Count of Categorical label
```python
sns.countplot(data['education_level']);
```

## Plot Count of Categorical Label Grouped-by Another Label
```python
chart = sns.catplot(x="education_level", kind="count", hue="income", data=data)
chart.set_xticklabels(rotation=90)
```

## Explore Pairwise Relationships in Data + Univariate Distribution of Each Feature (Numerical Features Only)
```python
import seaborn as sns

%matplotlib inline
sns.set(style="ticks")

sns.pairplot(data);

# Additional Option: Group data by a 3rd feature
sns.pairplot(data, hue="y");
```
Ref: [https://seaborn.pydata.org/generated/seaborn.pairplot.html#seaborn.pairplot](https://seaborn.pydata.org/generated/seaborn.pairplot.html#seaborn.pairplot)

## Plot Distribution of Numerical Features
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(20, 6))

chart1 = sns.distplot(data[["age"]])
chart1.set(xlabel="age", ylabel="dstribution")

chart2 = sns.catplot(x="age", kind="count", data=data)
#chart2.set(xticks=[20, 50, 90])
chart2.set(xticks=data['age'].values)
chart2.fig.set_figwidth(20)

print(data.loc[data['age'] < 17].shape)
```

## Plot Distribution of Categorical Features
```python
chart = sns.catplot(x="education_level", kind="count", data=data)
chart.set(xlabel="education_level", ylabel="count")
chart.set_xticklabels(rotation=90)
```

# Anaconda

## List envs
```shell
conda info --envs
```

## Activate env
```shell
conda activate default37
```

## Update all packages
```shell
congra upgrade -all
```

## Install package
```shell
conda install package_name

## specifying package version
conda install numpy=1.10
```

## Remove package
```shell
conda remove package_name
```

## Search package
```shell
conda search *search_term*
```

## List packages
```shell
conda list
```

# Jupyter

## Convert notebook to html
```shell
jupyter nbconvert --to html notebook.ipynb

# Other formats
# https://nbconvert.readthedocs.io/en/latest/usage.html
```

## Add TOC
Ref: [https://towardsdatascience.com/jupyter-tools-to-increase-productivity-7b3c6b90be09](https://towardsdatascience.com/jupyter-tools-to-increase-productivity-7b3c6b90be09)