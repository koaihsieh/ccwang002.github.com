---
layout: post
title: "Web Conf-Day2"
date: 2013-01-13 10:55
comments: true
categories: 
 - note
 - conf
---
<!-- more -->
### HTTP/1.1 Pipeline

* Head of Line Blocking
* Client 不知 server 有沒有支援

### Multiple TCP connection
* 第一個request要熱身
    * handshake, slow start
* 但會互相競爭，且都要熱身


### SPDY