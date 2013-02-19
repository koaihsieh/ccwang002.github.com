---
layout: post
title: "Scipy 0.12.0b1 on Python 3.3 on OSX 10.7"
date: 2013-01-27 04:13
comments: true
categories: 
 - python
 - note
---

### Requirement
* Homebrew python 3.3.0
* tap [Samuel John's formula repo](https://github.com/samueljohn/homebrew-python)
* use GNU Fortran
* use OpenBLAS instead of Apple's accelerate framework.

<!-- more -->

{% codeblock lang:bash %}
$ brew install python3
$ brew tap samueljohn/python    # tap samueljohn's repo
$ brew install gfortran openblas         # install GNU fortran and OpenBLAS
{% endcodeblock %}

### Install Scipy 0.12.0b1
First one will need Numpy, 1.7.0 will be good.  
Current stable version of Scipy is 0.11, which is not worked on Python 3. Scipy's library `weave` only supports python 2.

{% codeblock lang:bash %}
# for safety, use virtualenv
$ pip-3.3 install nose virtualenv

# set up virtual environment
$ virtualenv-3.3 --system-site-packages test_scipy  # or one can reinstall numpy here
$ cd test_scipy
$ source bin/activate
$ which python3     # should be .../test_scipy/bin/python3
$ which pip3        # should be .../test_scipy/bin/pip3


# setup environment variables
(test_scipy)$ export ATLAS=None
# get the location of OpenBLAS library
(test_scipy)$ locate libopenblas.dylib
# for example /usr/local/Cellar/openblas/0.2.5/lib/libopenblas.dylib
(test_scipy)$ export LAPACK=/usr/local/Cellar/openblas/0.2.5/lib/libopenblas.dylib
(test_scipy)$ export BLAS=/usr/local/Cellar/openblas/0.2.5/lib/libopenblas.dylib
{% endcodeblock %}

Then we can build Scipy from source.  

{% codeblock lang:bash %}
# get source from http://sourceforge.net/projects/scipy
(test_scipy)$ wget http://sourceforge.net/projects/scipy/files/scipy/0.12.0b1/scipy-0.12.0b1.tar.gz && tar zxvf scipy-0.12.0b1.tar.gz
(test_scipy)$ cd scipy-0.12.0b1
# check configuration
(test_scipy)$ python3 setup.py config
# installation
(test_scipy)$ python3 setup.py install
{% endcodeblock %}


### Test

{% codeblock lang:bash %}
(test_scipy)$ python3
>>> import scipy
>>> scipy.test()
NumPy version 1.7.0
SciPy version 0.12.0b1
SciPy is installed in /Users/liang/test_scipy/lib/python3.3/site-packages/scipy
…… 
…… 
…… 
…… (messy messages here)
======================================================================
ERROR: Failure: ImportError (scipy.weave only supports Python 2.x)
    raise ImportError("scipy.weave only supports Python 2.x")
ImportError: scipy.weave only supports Python 2.x

(blablabla ...)
{% endcodeblock %}

### Configuration Output
The configuration by `python3 setup.py config` will be something like:

```
Disabled atlas_blas_threads_info: (ATLAS is None)
  libraries openblas not found in []
  NOT AVAILABLE

atlas_blas_info:
Disabled atlas_blas_info: (ATLAS is None)
  libraries openblas not found in []
  NOT AVAILABLE

# --- (Skipped) ---
blas_info:
Replacing _lib_names[0]=='blas' with 'openblas'
Replacing _lib_names[0]=='openblas' with 'openblas'
  FOUND:
    language = f77
    library_dirs = ['/usr/local/Cellar/openblas/0.2.5/lib']
    libraries = ['openblas']

  FOUND:
    define_macros = [('NO_ATLAS_INFO', 1)]
    language = f77
    library_dirs = ['/usr/local/Cellar/openblas/0.2.5/lib']
    libraries = ['openblas']

lapack_opt_info:
lapack_mkl_info:
mkl_info:
  libraries mkl,vml,guide not found in ['/Users/liang/test_scipy/bin/../lib', '/usr/local/lib', '/usr/lib']
  NOT AVAILABLE

  NOT AVAILABLE
  
 
umfpack_info:
amd_info:
  FOUND:
    define_macros = [('SCIPY_AMD_H', None)]
    include_dirs = ['/usr/local/include']
    library_dirs = ['/usr/local/lib']
    libraries = ['amd']
    swig_opts = ['-I/usr/local/include']

  FOUND:
    define_macros = [('SCIPY_UMFPACK_H', None), ('SCIPY_AMD_H', None)]
    include_dirs = ['/usr/local/include']
    library_dirs = ['/usr/local/lib']
    libraries = ['umfpack', 'amd']
    swig_opts = ['-I/usr/local/include', '-I/usr/local/include']
```

