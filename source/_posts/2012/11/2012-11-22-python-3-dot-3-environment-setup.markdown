---
layout: post
title: "Python 3.3 Environment Setup"
date: 2012-11-22 11:02
comments: true
categories: 
 - lab log
 - python
---

### Python 3.3 installation
* Using `pythonbrew` for installation.
* more refer to [here](https://github.com/utahta/pythonbrew)
  
{% codeblock lang:bash%}
$ curl -kL http://xrl.us/pythonbrewinstall | bash
# add the following lines in ~/.bash_profile
$ pythonbrew install 2.7.3 3.2
$ python brew switch 2.7.3
{% endcodeblock %}

<!-- more -->

### Numpy
So far not stable. Fail in the test.

{% codeblock lang:bash%}
$ export CC=clang
$ export CXX=clang
$ export FFLAGS=-ff2c
$ git clone https://github.com/numpy/numpy.git
$ cd numpy
$ python3 setup.py build
$ python3 setup.py install 
{% endcodeblock %}


### Subprocess
Tutorials: 

* <http://blog.sina.com.cn/s/blog_64d75a250100i9tv.html>



