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

# ttest
$ ttest ahe if year == 2008, by(bachelor)
# first one should assume they have unequal variance
$ …, uneuqal/welch

# prtest
$ prtest bachelor==0.4 if year==2008

# 0, 1, 0, 1, 1, 0, 0, …, = Bernoulli RV, E(B. RV) = p of B. RV
# pr test, H0: bachelor == mean (=p of B.RV)

{% endcodeblock %}