---
layout: page
title: "Environment Setup in Mac"
date: 2012-10-19 20:44
comments: true
sharing: true
footer: true
---

## Softwares Preparation

* Xcode
* Homebrew: Package Management
* Text editor: Sublime, Vim and etc.
* Perlbrew(*exp*): Perl version management
* iTerm2: more powerful terminal
* Filezilla: (S)FTP file transfer


## Installation Instruction

### Xcode 4.5.1
* Download Xcode from [developer's site][xcode] or directly from Mac App Store.
* After install Xcode, an additional **Command Line Tool** package of developer tools is required.  
![](/note/pic/xcode_clt.png)
![](/note/pic/xcode_dev.png)
[xcode]: https://developer.apple.com/xcode/
* Or one can get/check the same(? not quite sure, use `$ brew doctor` to check) CLT package through Xcode itself.  
![](/note/pic/xcode_preference.png)  
![](/note/pic/xcode_component.png)  

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

* If any error or warning comes up, simply follow the given instructions.
* Google/Stack Overflow contains numerous solutions and Q&A for homebrew installation and usage.

[homebrew]: http://mxcl.github.com/homebrew/

### Text Editor

* Sublime Text 2: [homepage][sublime2]
* MacVim: [homepage][macvim]

[sublime2]: http://www.sublimetext.com/
[macvim]: http://code.google.com/p/macvim/

### Terminal Alternatives

* iTerm2: [homepage][iterm2]

[iterm2]: http://www.iterm2.com/

### Perlbrew (*Experimental*)
* [homepage][perlbrew], and a chinese introduction [here](http://perlbrew.pl/Perlbrew-%E4%B8%AD%E6%96%87%E7%B0%A1%E4%BB%8B.html).
* Install multiple version of perl, similar to rbenv.

{%codeblock lang:bash%}
# Change the perlbrew directory same as the homebrew
$ export PERLBREW_ROOT=/usr/local/Cellar/perl5
$ curl -kL http://install.perlbrew.pl | bash
{%endcodeblock%}

* One should modify ones bash profile such as `~/.bash_profile` by adding 
{%codeblock lang:bash%}
# perlbrew
export PERLBREW_ROOT=/usr/local/Cellar/perl5
. /usr/local/Cellar/perl5/etc/bashrc
{%endcodeblock%}

* To install the latest stable release
{%codeblock lang:bash%}
$ perlbrew install perl-5.16.0
$ perlbrew switch perl-5.16.0
{%endcodeblock%}

[perlbrew]: http://perlbrew.pl/