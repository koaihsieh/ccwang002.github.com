---
layout: post
title: "Python Environment Setup"
date: 2012-11-22 11:02
comments: true
categories: 
 - lab log
 - python
---

## Python 3.3 & 3.2.3 installation

Reference: <http://stackoverflow.com/questions/398768>

### [Way 1] 如果是自動 brew upgrade 升級就是這種

{% codeblock lang:bash%}
$ brew versions python3
3.3.0 git checkout bdaae65 /usr/local/Library/Formula/python3.rb
3.2.3 git checkout 0f4a4af /usr/local/Library/Formula/python3.rb
...
# 現在會裝成 Python3.3
$ brew install python3

# 裝上 Python3.2
$ cd /usr/local/Library/Formula/
$ git checkout 0f4a4af /usr/local/Library/Formula/python3.rb
$ brew unlink python3
$ brew install python3

# 自由切換
$ brew switch python3 3.2.3
Cleaning /usr/local/Cellar/python3/3.2.3
Cleaning /usr/local/Cellar/python3/3.3.0
14 links created for /usr/local/Cellar/python3/3.2.3

$ brew switch python3 3.3.0
Cleaning /usr/local/Cellar/python3/3.2.3
Cleaning /usr/local/Cellar/python3/3.3.0
15 links created for /usr/local/Cellar/python3/3.3.0

# 想要同時使用舊版的話，可以直接繼續 [Way2]
{% endcodeblock %}
<!-- more -->
### [Way2] 同時做用 3.3.0 & 3.2.3
{% codeblock lang:bash%}
$ brew tap homebrew/versions
$ brew install python32
# 這樣設定的話，python3 依然link到最新版3.3.0
$ python3 -V
Python 3.3.0
# 用舊版要使用版本號 python3.2
$ python3.2 -V
{% endcodeblock %}

之後的設定，選用 python3 -> Python 3.3.0, python3.2 -> Python 3.2.3

### Numpy 1.7.0b2
{% codeblock lang:bash%}
$ wget http://sourceforge.net/projects/numpy/files/NumPy/1.7.0b2/numpy-1.7.0b2.tar.gz
$ tar zxvf numpy-1.7.0b2.tar.gz
$ cd numpy-1.7.0b2
$ python3 setup.py build
$ python3 setup.py install
# testingNG
$ cd
$ py3 
>>> import numpy as np
>>> np.test()
{% endcodeblock %}

重點是要選對numpy的版本

### Scipy
Currently I cannot build it successfully using version either 0.11.0(stable) or the develop version(git)