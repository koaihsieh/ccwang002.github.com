---
layout: page
title: "Environment Setup in Mac"
date: 2012-10-19 20:44
comments: true
sharing: true
footer: true
---

## Softwares Preparation

### Xcode 4.5.1
* Download Xcode from [developer's site][xcode] or directly from Mac App Store.
* After install Xcode, an additional **Command Line Tool** package of developer tools is required.  
![](/note/pic/xcode_clt.png)
![](/note/pic/xcode_dev.png)
[xcode]: https://developer.apple.com/xcode/
* To test installation, open the Terminal and type
{%codeblock lang:bash%}
$ gcc --version
# if installed successfully
i686-apple-darwin11-llvm-gcc-4.2 (GCC) 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2336.11.00)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
{%endcodeblock%}


### Homebrew
* [mainpage][homebrew]
* quick installation

{%codeblock lang:bash%}
$ ruby -e "$(curl -fsSkL raw.github.com/mxcl/homebrew/go)"
# check homebrew environment
$ brew doctor
# if all is set up
Your system is raring to brew.
{%endcodeblock%}

[homebrew]: http://mxcl.github.com/homebrew/

### Text Editor

* Sublime Text 2: [homepage][sublime2]
* MacVim: [macvim]

[sublime2]: http://www.sublimetext.com/
[macvim]: http://code.google.com/p/macvim/