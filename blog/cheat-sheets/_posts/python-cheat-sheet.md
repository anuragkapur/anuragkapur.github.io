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