---
layout: post
title: "Learn Django"
date: 2013-05-28 19:29
comments: true
categories: 
 - note
 - django
 - python
---

### PIP setup

{% codeblock lang:bash%}
$ export PIP_DOWNLOAD_CACHE=/path/to/cache
{% endcodeblock %}

在 pip 當中設定 requirements

{% codeblock lang:bash%}
$ pip install -r /path/to/requirements.txt
{% endcodeblock %}


### Django
1.5 supports Python3, but 1.4 don't

### Django on Windows
Before install Django

* install PowerShell
* install Python
* install pip
* install Django
* run server

Windows package manager <http://chocolatey.org/>

* 環境變數設定 Python 以及 Python script
* 使用 `get-pip.py` 腳本安裝 pip
* download django
* run `install-django.py`

