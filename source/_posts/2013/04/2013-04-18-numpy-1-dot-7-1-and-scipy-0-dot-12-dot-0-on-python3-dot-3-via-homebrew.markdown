---
layout: post
title: "Numpy 1.7.1 and Scipy 0.12.0 on Python3.3 via Homebrew"
date: 2013-04-18 14:11
comments: true
categories: 
 - python
 - note
---

### Requirement and System info
* Mac OSX 10.7.5
* Xcode 4.6.1
* gfortran 4.8.0 (via Homebrew)

If one have previously installed these packages but older version, it is recommended to reinstall them again (including all packages compiled by gfortran). Here Numpy can facilitates packages LAPACK and BLAS. 

<!-- more -->
{% codeblock lang:bash %}
# update your brew repo first
$ brew update
# install the latest gfortran version
$ brew install gfortran
$ brew install swig

# reinstall LAPACK and BLAS. In Mac it is OpenBLAS
$ brew uninstall openblas
$ brew install openblas

# get numpy 1.7.1 from sourceforge 
$ wget http://sourceforge.net/projects/numpy/files/NumPy/1.7.1/numpy-1.7.1.tar.gz
$ tar zxvf numpy-1.7.1.tar.gz
$ cd numpy-1.7.1

# basic environment configuration
$ locate openblas.dylib     # at this time I have version 0.2.6
# /usr/local/Cellar/openblas/0.2.6/lib/libopenblas.dylib

$ export ALTAS=None
$ export LAPACK=/usr/local/Cellar/openblas/0.2.6/lib/libopenblas.dylib
$ export BLAS=/usr/local/Cellar/openblas/0.2.6/lib/libopenblas.dylib
$ python3 setup.py install

# you need nose to test numpy
# nose can be installed by pip
$ pip-3.3 install nose
$ python3 -c "import numpy; numpy.test()"
# My test result is shown as follows
# OK (KNOWNFAIL=6, SKIP=5)
# <nose.result.TextTestResult run=4789 errors=0 failures=0>

# install scipy 0.12.0
$ wget http://sourceforge.net/projects/scipy/files/scipy/0.12.0/scipy-0.12.0.tar.gz
$ tar zxvf scipy-0.12.0.tar.gz
$ cd scipy-0.12.0
# set the environment configuration as previously mentioned
$ python3 setup.py install
$ python3 -c "import scipy; scipy.test()"
# My test result (though failed, the result looks fine to me)
# Ran 5964 tests in 86.774s
# FAILED (KNOWNFAIL=16, SKIP=44, errors=2)
# ERROR: Failure: ImportError (cannot import name periodogram)
# ERROR: Failure: ImportError (scipy.weave only supports Python 2.x)
{% endcodeblock %}

