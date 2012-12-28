---
layout: post
title: "Python 2.7.3 Hombrew"
date: 2012-12-28 14:27
comments: true
categories: 
 - note
 - python
---

## Summary
Mac Lion 10.7.5

* Python 2.7.3
* Numpy 1.6.2 (1.7.0b2)
* Scipy 0.11.0
* IPython 0.13.1
* matplotlib 1.2.0

<!-- more -->

## Install python 2.7.3 using homebrew

{% codeblock lang:bash %}
$ brew install gfortran
$ brew install umfpack
$ brew install python
$ pip install nose

# Thanks to Mr. Samuel for creating these helpful receipts
$ brew tap samueljohn/python
# install numpy 1.6.2, --devel will install 1.7.0b2
$ brew install numpy --with-openblas 
$ brew install scipy --with-openblas
$ pip install matplotlib
$ pip install tornado
$ pip install pyzmq
$ pip install ipython

# testing 
$ python
>>> import numpy as np
>>> np.test()
OK (KNOWNFAIL=5, SKIP=5)
<nose.result.TextTestResult run=3523 errors=0 failures=0>

>>> import scipy
>>> scipy.test()
OK (KNOWNFAIL=10, SKIP=27)
<nose.result.TextTestResult run=4230 errors=0 failures=0>

>>> import matplotlib
>>> matplotlib.test()
Ran 1214 tests in 352.656s
OK (KNOWNFAIL=301)

{% endcodeblock %}


detailed version by `$ pip-2.7 freeze`.

* distribute==0.6.32
* ipython==0.13.1
* matplotlib==1.2.0
* nose==1.2.1
* numpy==1.6.2
* pyzmq==2.2.0.1
* scipy==0.11.0
* tornado==2.4.1
* wsgiref==0.1.2