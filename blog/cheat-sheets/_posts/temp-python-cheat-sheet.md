<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Installing and configuring pyenv](#installing-and-configuring-pyenv)
- [Install a specific python version](#install-a-specific-python-version)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Installing and configuring pyenv
```
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'eval "$(pyenv init --path)"' >> ~/.zshrc

pyenv install 3.7.3
pyenv global 3.7.3

python --version
pip --version
```

## Install a specific python version
```
# install
pyenv install -v 2.7.18

# use
pyenv local 2.7.18

# verify
python --version
```