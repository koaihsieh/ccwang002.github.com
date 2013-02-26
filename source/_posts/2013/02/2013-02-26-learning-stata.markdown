---
layout: post
title: "Learning STATA"
date: 2013-02-26 14:52
comments: true
categories: 
 - note
 - stata
---

### Basic usage

<!-- more -->
{% codeblock lang:bash %}

# import data
$ insheet
$ use
$ infix

# clear dataset
$ clear

$ drop var1 var2 …
$ drop var1-var10
$ keep

# adding conditions
$ keep if <condition>
$ drop if <condition>

# generate new variable
$ gen newvar = <statement on old var>
$ gen var2 = var^2
$ gen varlog = log(var)

# string manipulation
$ gen str varstr = string(var1) + "test"

$ replace var1 = <statement>
$ rename var1 newvar1name

# missing value = .
$ replace missingvar=0 if missingvar==.
$ gen var=var2>1    # 0 or 1

# label


{% endcodeblock %}