---
layout: post
title:  "Python cheat sheet"
teaser: Python Cheat Sheet - Pandas, Numpy, Anaconda, Jupyter
date:   2020-04-19 00:00:00 +0000
categories: cheat-sheets
tags: cheat-sheets
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Pandas](#pandas)
  - [Read CSV as a DataFrame](#read-csv-as-a-dataframe)
  - [Drop a column from DF](#drop-a-column-from-df)
  - [# Log-transform the skewed features](#-log-transform-the-skewed-features)
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

## Drop a column from DF
```python
features_raw = data.drop('<column_name>', axis = 1) # axis = 1 => axis = 'columns'
```

## Log-transform the skewed features
```python
skewed = ['<feature_column_name_1>', '<feature_column_name_2>']
features_log_transformed = pd.DataFrame(data = features_raw)
features_log_transformed[skewed] = features_raw[skewed].apply(lambda x: np.log(x + 1))
```

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