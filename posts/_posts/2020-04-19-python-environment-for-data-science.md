---
layout: post
date: 2020-04-19
title: "How to set up a python environment for data science or anything else"
category: posts
tags: [python, devops]
published: true
share: false
author: namkhanhtran
description: "Notes on setting up a python environment"
---

## Introduction
Coding in Python is awesome and is getting more awesome with every new release! This is mainly due to the massive amount of freely available libraries,
its readability, and the recently introduced type annotations. However, maintaining a big python project still keeps very challenging, especially because 
of versioning issue. In big companies (Amazon, Google, Facebook), there are a bunch of different ways to handle this issue. Here is a list of tools that
can be used to ease this pain. 

This post aims to keep notes for myself. The content is relied heavily on a great [post](https://towardsdatascience.com/how-to-setup-an-awesome-python-environment-for-data-science-or-anything-else-35d358cc95d5).

### The python environment
Options
- [x] anaconda
- [x] pip
- [x] [pyenv](https://github.com/pyenv/pyenv)

Most of the time I have been using anaconda and pip, but pyenv is also a great tool to manage python intepreters.

* Install 

  ```python
  curl https://pyenv.run | bash
  ```

* Add `pyenv` to PATH

  ```python
  export PATH="~/.pyenv/bin:$PATH"
  eval "$(pyenv init -)"
  eval "$(pyenv virtualenv-init -)"
  ```

* Install a python intepreter

  ```python
  pyenv install VERSION_YOU_WOULD_LIKE_TO_INSTALL
  pyenv install --list
  pyenv global 3.7.5 # make it a default global intepreter
```
  
  

### Dependency Management

Options

- [x] pip/anaconda
- [ ] [poetry](https://python-poetry.org/)

So far I've been using pip/anaconda to manage project dependencies, which is sometimes very messy and painful. `poetry` is the tool that I've been tried to help me get rid of this pain (still exploring this tool).

* Install

  ```bash
  curl -sSL https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py | python
  ```

  ```bash
  # Another way
  # Create a virtual environment called tools that is based on 3.7.5
  pyenv virtualenv 3.7.5 tools 
  # Install poetry into the tools virtual env
  pyenv activate tools
  pip install poetry 
  # Check installed poetry version
  poetry --version
  # Leave the virtual env 
  pyenv deactivate 
  # This does not work yet 
  poetry --version
  # Add your tools virtual env to the globally available ones
  pyenv global 3.7.5 tools
  # Now this works and you can start using poetry
  poetry --version
  ```

* Configure

  ```bash
  # create `.venv` folder inside the project directory --> IDEs (Pycharm) recognizes the correct intepreter more easily
  poetry config virtualenvs.in-project true
  ```

* Create new project

  ```python
  # Initialze a new project
  poetry new dsexample
  cd dsexample
  # Add modules and create virtual environment.
  poetry add pandas=0.25 fastapi --extras all
  # As an example of how you could add a git module
  poetry add tf2-utils --git git@github.com:Shawe82/tf2-utils.git
  ```


## Links
1. [https://towardsdatascience.com/how-to-setup-an-awesome-python-environment-for-data-science-or-anything-else-35d358cc95d5](https://towardsdatascience.com/how-to-setup-an-awesome-python-environment-for-data-science-or-anything-else-35d358cc95d5)

