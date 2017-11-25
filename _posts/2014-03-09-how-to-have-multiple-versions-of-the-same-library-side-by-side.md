---
layout: post
title: "How to Have Multiple Versions of C++ OpenCV Side by Side"
description: ""
tags: [Linux, C++, OpenCV, Programming]
---

*This post was originally published on
<a href="http://code.litomisky.com/2014/03/09/how-to-have-multiple-versions-of-the-same-library-side-by-side/"
   target="_blank" title="Admiral Ackbar's Code Emporium">
   Admiral Ackbar's Code Emporium
</a>.*

This tutorial will show you how you can have different versions of the same library side by side such that it's easy to change which version your code uses.

For example, I work a lot with OpenCV, the computer vision library. I like to be able to try out different features in the trunk version of the library, but prefer to use a stable release in production settings. It's actually pretty easy to have both versions on your computer, and select which one you'd like to use at compile time. 

The following assumes you're on a Linux machine. I'll use OpenCV as an example, but the concept applies to any library.

<!--more-->


## Set up Both Versions of OpenCV

The big idea is that you don't want to "install" OpenCV into the system's default directories (/usr/lib or /usr/local/lib), since each version would place itself into an "opencv" directory, creating a big ol' mess.

I like to have a "libs" directory right under my home directory.
In this directory, create a separate directory for each OpenCV version. Let's say doing this, I created two directories:

   ~/libs/opencv-trunk
   ~/libs/opencv-2.4.8

Let's go through the compilation process for the trunk version of OpenCV:

**1. Create the directory where you want the output files to go:**

    cd ~/libs/opencv-trunk
    mkdir release
    cd release
    mkdir installed

I'll put mine under ~/libs/opencv-trunk/release/installed


**2. Tell CMake your compilation options**

    cmake -DCMAKE_INSTALL_PREFIX=/home/krystof/libs/opencv-trunk/release/installed -DCMAKE_BUILD_TYPE="Release" .. 

CMAKE_INSTALL_PREFIX is the directory where you want the final output files. I'm also telling CMake to compile the Release (optimized) version of the library; you might (and I do) want to have Release and Debug versions available.


**3. Compile!**

     make install

You can look under the install directory to verify that all the library files were created there.



## Create a Simple Test Program

Let's make sure our process worked.

Here's a simple program that prints the running OpenCV version:

main.cpp:

{% highlight cpp %}
#include <iostream>
#include "opencv2/core/version.hpp"

int main(int argc, char ** argv)
{
  std::cout << "OpenCV version: "
            << CV_MAJOR_VERSION << "." 
            << CV_MINOR_VERSION << "."
            << CV_SUBMINOR_VERSION
            << std::endl;
  return 0;
}
{% endhighlight %}


Makefile:
{% highlight makefile %}
CPP = g++

# OpenCV trunk
CPPFLAGS = -L/home/krystof/libs/opencv-trunk/release/installed/libs \
	   -I/home/krystof/libs/opencv-trunk/release/installed/include \
	   -Wl,-rpath=/home/krystof/libs/opencv-trunk/release/installed/libs

# Opencv 2.4.8
#CPPFLAGS = -L/home/krystof/libs/opencv-2.4.8/release/installed/libs \
            -I/home/krystof/libs/opencv-2.4.8/release/installed/include \
	    -Wl,-rpath=/home/krystof/libs/opencv-2.4.8/release/installed/libs

all: test

test: main.cpp
      $(CPP) $(CPPFLAGS) $^ -o $@
{% endhighlight %}


Make sure you adjust the paths in the Makefile to match your own, based on where you installed the different OpenCV versions.

The purpose of the individual flags under CPPFLAGS is as follows:
- `-L` add this directory to the list of places to look for precompiled libraries (.so files) when linking
- `-I` add this directory to the list of places to look for headers (files you `#include`)
- `--Wl,-rpath` specifies the run-time path of the library. This should be the same as the path set by the `-L` flag

Based on which `CPPFLAGS` line in the Makefile you leave in, you should get one of the following outputs when you run the `test` executable you just created:

    OpenCV version: 2.4.8

or

    OpenCV version: 3.0.0

3.0.0 is the output from the trunk version here.

If you are having trouble with the linking portion, you may find
[this post](http://gcc.gnu.org/ml/gcc-help/2005-12/msg00017.html)
helpful.

So there you go! All you have to do is change one line in a Makefile, and your code gets compiled with different versions of OpenCV!

If you found this post helpful, please let me know by commenting below. Thanks!
