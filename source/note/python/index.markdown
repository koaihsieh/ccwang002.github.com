---
layout: page
title: "Learning Python"
date: 2013-01-14 22:40
comments: true
sharing: true
footer: true
---

投影片：[這裡](http://ccwang002.github.com/python-tutorial-slides/)

這邊主要整理了一些我打算講的內容的大綱，日後做成投影片之用。   
使用的教材主要是參考 [Dive in Python 3][dive] 以及 [Learning Python 4ed](http://shop.oreilly.com/product/9781565924642.do)。前者是一個網站，後者是一本書，中文有第3版的但絕版了（我有可以找我拿），英文的我也有。

[dive]:http://getpython3.com/

## Environment Setting
See [The Hitchhiker's Guide to Python][guide].

* basic python 2.7.x, 3.3.x installation.  
One can install it using the official installer binaries, or compile it direct from source.

* `easy_install`, `pip` python package manager

* (Optional) usefull packages: `numpy`, `scipy`, `ipython`

### Coding Style

* See part of [coding style](https://python-guide.readthedocs.org/en/latest/writing/style/) in The Hitchhiker's Guide to Python

* Official and generally accepted Python coding style is described in [PEP8][pep8]

* The Zen of Python (or [PEP20][pep20]), which can be printed by `import this`

[pep8]:http://www.python.org/dev/peps/pep-0008/
[pep20]:http://www.python.org/dev/peps/pep-0020/

### File handling

### Exception handling

* try ... except E1 (as err1) ... except E2 (as err2) ... else ... finally...

* more on [How to catch a expection @StackOverflow][excpetion]

[excpetion]: http://stackoverflow.com/questions/713794/catching-an-exception-while-using-a-python-with-statement

### Scientific Python
* [Scipy-lectures@Github](http://scipy-lectures.github.com/)

## Reference

* Overall Introduction of python using online resources: [The Hitchhiker’s Guide to Python][guide].

* perl, php, python, ruby syntax comparison sheet <http://hyperpolyglot.org/scripting>

* a graphical demonstration of running a python script. <http://www.pythontutor.com/>

* learn by interactive samples:  
    * <http://www.learnpython.org/>
    * <http://www.codecademy.com/tracks/python> (Recommended)
    
* collection of good to great examples of Python by Jesse Noller   
<http://jessenoller.com/good-to-great-python-reads/>

[guide]: http://docs.python-guide.org/en/latest/
