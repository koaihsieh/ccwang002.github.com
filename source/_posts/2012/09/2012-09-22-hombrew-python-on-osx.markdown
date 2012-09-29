---
layout: post
title: "Hombrew Python on OSX"
date: 2012-09-22 00:04
comments: true
categories: 
 - coding
 - note
---

Edit the file `.bash_profile`
```
# Python by Homebrew
export PATH=/usr/local/bin:/usr/local/share/python:$PATH
```

```
$ brew install python --framework
# check 
$ which python
/usr/bin/python
$ which pip
/usr/local/share/python/pip
```

<!-- more -->

```
liang@Liangs-MacBook-Air:~$ brew install python --framework
==> Downloading http://www.python.org/ftp/python/2.7.3/Python-2.7.3.tar.bz2
Already downloaded: /Library/Caches/Homebrew/python-2.7.3.tar.bz2
==> ./configure --prefix=/usr/local/Cellar/python/2.7.3 --enable-ipv6 --dataroot
==> make
==> make install PYTHONAPPSDIR=/usr/local/Cellar/python/2.7.3
==> make frameworkinstallextras PYTHONAPPSDIR=/usr/local/Cellar/python/2.7.3/sha
==> Downloading http://pypi.python.org/packages/source/d/distribute/distribute-0
Already downloaded: /Library/Caches/Homebrew/distribute-0.6.28.tar.gz
==> /usr/local/Cellar/python/2.7.3/bin/python setup.py --no-user-cfg install --f
==> Downloading http://pypi.python.org/packages/source/p/pip/pip-1.2.tar.gz
Already downloaded: /Library/Caches/Homebrew/pip-1.2.tar.gz
==> /usr/local/Cellar/python/2.7.3/bin/python setup.py --no-user-cfg install --f
==> Caveats
The Python framework is located at
  /usr/local/Cellar/python/2.7.3/Frameworks/Python.framework

You can find the Python demo at
  /usr/local/share/python/Extras

You can `brew linkapps` to symlink "Idle" and the "Python Launcher".

A "distutils.cfg" has been written, specifying the install-scripts folder as:
  /usr/local/share/python

If you install Python packages via "pip install x" or "python setup.py install"
(or the outdated easy_install), any provided scripts will go into the
install-scripts folder above, so you may want to add it to your PATH.

The site-package directory for brewed Python:
  /usr/local/lib/python2.7/site-packages

Distribute and Pip have been installed. To update them
  /usr/local/share/python/pip install --upgrade distribute
  /usr/local/share/python/pip install --upgrade pip

See: https://github.com/mxcl/homebrew/wiki/Homebrew-and-Python
==> Summary
/usr/local/Cellar/python/2.7.3: 5165 files, 80M, built in 80 seconds
```
One can still alias the python3 and pip for py3.

Python should be located at `/usr/bin/python`

* Documentation for `virtualenvwrapper` <http://virtualenvwrapper.readthedocs.org/en/latest/index.html>

### Numpy, Scipy

1. Compile `bumpy` from source
2. then install `scipy` by   
{% codeblock %}
$ pip install scipy
{% endcodeblock %}
3. test   
{% codeblock %}
$ python
>>> import numpy as np
>>> import scipy
>>> np.test("full")
>>> scipy.test()
{% endcodeblock %}

### IPython

* IPython Notebook  
<http://www.randalolson.com/2012/05/12/a-short-demo-on-how-to-use-ipython-notebook-as-a-research-notebook/>

### Matplotlib

some modifications needed in order to install it by `$pip install matplotlib`
* <http://stackoverflow.com/questions/4092994/unable-to-install-matplotlib-on-mac-os-x>

### OpenCV

<http://www.yasutomo57jp.com/2012/09/19/mac-osx-mountain-lion-%E3%81%AE-homebrew-%E3%81%A7-opencv-%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB/>

Need modification to brew successfully if one use the self-compiled python(ex 2.7.3)

    $ brew edit opencv

And change to the following script

{% codeblock lang:ruby %}
require 'formula'

def which_python
  "python" + `python -c 'import sys;print(sys.version[:3])'`.strip
end

def site_package_dir
  "lib/#{which_python}/site-packages"
end

class Opencv < Formula
  homepage 'http://opencv.org/'
  url 'http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.4.2/OpenCV-2.4.2.tar.bz2'
  sha1 '96ff27b87e0f028d1d16201afebabec4e0c72367'

  option '32-bit'
  option 'with-qt',  'Build the Qt4 backend to HighGUI'
  option 'with-tbb', 'Enable parallel code in OpenCV using Intel TBB'

  depends_on 'cmake' => :build
  depends_on 'pkg-config' => :build
  depends_on 'numpy' => :python

  depends_on 'eigen'   => :optional
  depends_on 'libtiff' => :optional
  depends_on 'jasper'  => :optional
  depends_on 'tbb'     => :optional
  depends_on 'qt' if build.include? 'with-qt'
  depends_on :libpng

  # Can also depend on ffmpeg, but this pulls in a lot of extra stuff that
  # you don't need unless you're doing video analysis, and some of it isn't
  # in Homebrew anyway. Will depend on openexr if it's installed.

  def install
    args = std_cmake_args + %w[
      -DWITH_CUDA=OFF
      -DBUILD_ZLIB=OFF
      -DBUILD_TIFF=OFF
      -DBUILD_PNG=OFF
      -DBUILD_JPEG=OFF
      -DBUILD_JASPER=OFF
      -DBUILD_TESTS=OFF
      -DBUILD_PERF_TESTS=OFF
    ]
    if build.build_32_bit?
      args << "-DCMAKE_OSX_ARCHITECTURES=i386"
      args << "-DOPENCV_EXTRA_C_FLAGS='-arch i386 -m32'"
      args << "-DOPENCV_EXTRA_CXX_FLAGS='-arch i386 -m32'"
    end
    args << '-DWITH_QT=ON' if build.include? 'with-qt'
    args << '-DWITH_TBB=ON' if build.include? 'with-tbb'

    # The CMake `FindPythonLibs` Module is dumber than a bag of hammers when
    # more than one python installation is available---for example, it clings
    # to the Header folder of the system Python Framework like a drowning
    # sailor.
    #
    # This code was cribbed from the VTK formula and uses the output to
    # `python-config` to do the job FindPythonLibs should be doing in the first
    # place.
    python_prefix = "/usr/local/Cellar/python/2.7.3/Frameworks/Python.framework/Versions/2.7"
    # Python is actually a library. The libpythonX.Y.dylib points to this lib, too.
    if File.exist? "#{python_prefix}/Python"
      # Python was compiled with --framework:
      args << "-DPYTHON_LIBRARY='#{python_prefix}/Python'"
      args << "-DPYTHON_INCLUDE_DIR='#{python_prefix}/Headers'"
    else
      python_lib = "#{python_prefix}/lib/lib#{which_python}"
      args << "-DPYTHON_LIBRARY='#{python_lib}.dylib'"
      args << "-DPYTHON_INCLUDE_DIR='#{python_prefix}/include/#{which_python}'"
    end
    args << "-DPYTHON_PACKAGES_PATH='#{python_prefix}/lib/python2.7/site-packages'"

    args << '..'
    mkdir 'macbuild' do
      system 'cmake', *args
      system "make"
      system "make install"
    end
  end

  def caveats; <<-EOS.undent
    The OpenCV Python module will not work until you edit your PYTHONPATH like so:
      export PYTHONPATH="#{HOMEBREW_PREFIX}/#{site_package_dir}:$PYTHONPATH"

    To make this permanent, put it in your shell's profile (e.g. ~/.profile).
    EOS
  end
end
{% endcodeblock %}



### Reference

* <http://penandpants.com/2012/02/24/install-python/>
* <http://note.sicafe.net/macPackageManageTips/html/homebrewPythonInstall.html>
* Talking about some `virtualenv`  
<http://superuser.com/questions/388854/the-suggested-way-to-handle-pipeasy-install-with-homebrew>
* <http://www.tlswebsolutions.com/mac-os-x-lion-setting-up-django-pip-virtualenv-and-homebrew/>