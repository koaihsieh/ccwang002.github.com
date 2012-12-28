---
layout: post
title: "Python 2.7 and 3.3 on CentOS 5"
date: 2012-12-28 16:00
comments: true
categories: 
 - python
 - note
 - centos
---

For CentOS 5, compiled python 2.7, 3.3 from source.  
One can refer to instructions from [server setup](/blog/2012/11/26/work-log-11-slash-26/)

{% codeblock lang:bash %}
# install dependencies for scipy and numpy
$ sudo yum install atlas-devel lapack-devel blas-devel

# install easy_install on both 2.7 and 3.3
$ curl -O http://python-distribute.org/distribute_setup.py
$ python distribute_setup.py
$ python3 distribute_setup.py

# install pip
$ easy_install-2.7 pip
$ esay_install-3.3 pip

# install numpy scipy ipython
$ sudo pip-2.7 install nose numpy scipy ipython
$ sudo pip-3.3 install nose numpy scipy ipython
{% endcodeblock %}