---
layout: post
title: "Hombrew Python on OSX"
date: 2012-09-22 00:04
comments: true
categories: 
 - coding
 - note
---

Edit the file `.bash_profile`
```
# Python by Homebrew
export PATH=/usr/local/bin:/usr/local/share/python:$PATH
```

```
$ brew install python --framework
# check 
$ which python
/usr/bin/python
$ which pip
/usr/local/share/python/pip
```
<!-- more -->
```
liang@Liangs-MacBook-Air:~$ brew install python --framework
==> Downloading http://www.python.org/ftp/python/2.7.3/Python-2.7.3.tar.bz2
Already downloaded: /Library/Caches/Homebrew/python-2.7.3.tar.bz2
==> ./configure --prefix=/usr/local/Cellar/python/2.7.3 --enable-ipv6 --dataroot
==> make
==> make install PYTHONAPPSDIR=/usr/local/Cellar/python/2.7.3
==> make frameworkinstallextras PYTHONAPPSDIR=/usr/local/Cellar/python/2.7.3/sha
==> Downloading http://pypi.python.org/packages/source/d/distribute/distribute-0
Already downloaded: /Library/Caches/Homebrew/distribute-0.6.28.tar.gz
==> /usr/local/Cellar/python/2.7.3/bin/python setup.py --no-user-cfg install --f
==> Downloading http://pypi.python.org/packages/source/p/pip/pip-1.2.tar.gz
Already downloaded: /Library/Caches/Homebrew/pip-1.2.tar.gz
==> /usr/local/Cellar/python/2.7.3/bin/python setup.py --no-user-cfg install --f
==> Caveats
The Python framework is located at
  /usr/local/Cellar/python/2.7.3/Frameworks/Python.framework

You can find the Python demo at
  /usr/local/share/python/Extras

You can `brew linkapps` to symlink "Idle" and the "Python Launcher".

A "distutils.cfg" has been written, specifying the install-scripts folder as:
  /usr/local/share/python

If you install Python packages via "pip install x" or "python setup.py install"
(or the outdated easy_install), any provided scripts will go into the
install-scripts folder above, so you may want to add it to your PATH.

The site-package directory for brewed Python:
  /usr/local/lib/python2.7/site-packages

Distribute and Pip have been installed. To update them
  /usr/local/share/python/pip install --upgrade distribute
  /usr/local/share/python/pip install --upgrade pip

See: https://github.com/mxcl/homebrew/wiki/Homebrew-and-Python
==> Summary
/usr/local/Cellar/python/2.7.3: 5165 files, 80M, built in 80 seconds
```
One can still alias the python3 and pip for py3.

Python should be located at `/usr/bin/python`

* Documentation for `virtualenvwrapper` <http://virtualenvwrapper.readthedocs.org/en/latest/index.html>

### Numpy, Scipy

1. Compile `bumpy` from source
2. then install `scipy` by   
{% codeblock %}
$ pip install scipy
{% endcodeblock %}
3. test   
{% codeblock %}
$ python
>>> import numpy as np
>>> import scipy
>>> np.test("full")
>>> scipy.test()
{% endcodeblock %}

### IPython

* IPython Notebook  
<http://www.randalolson.com/2012/05/12/a-short-demo-on-how-to-use-ipython-notebook-as-a-research-notebook/>

### Reference

* <http://penandpants.com/2012/02/24/install-python/>
* <http://note.sicafe.net/macPackageManageTips/html/homebrewPythonInstall.html>
* Talking about some `virtualenv`  
<http://superuser.com/questions/388854/the-suggested-way-to-handle-pipeasy-install-with-homebrew>
* <http://www.tlswebsolutions.com/mac-os-x-lion-setting-up-django-pip-virtualenv-and-homebrew/>