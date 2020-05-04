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

# Data Visualisation

## Draw Distribution of a Column Value
todo

# Anaconda

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