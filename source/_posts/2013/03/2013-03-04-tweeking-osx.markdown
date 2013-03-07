---
layout: post
title: "Tweeking OSX"
date: 2013-03-04 22:25
comments: true
categories: 
 - mac
 - note
---

Reference: <http://www.tuaw.com/2011/07/26/hackinations-5-really-good-lion-tweaks/>

### Changing expose speed

{% codeblock lang:bash %}
$ defaults write com.apple.dock expose-animation-duration -float 0.05; killall Dock
{% endcodeblock %}
