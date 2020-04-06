---
layout: post
title: "An Easy-To-Use Script to Install OpenCV for C++ and Python"
description: "An Easy-To-Use Script to Install OpenCV for C++ and Python"
tags: [Software, Linux, OpenCV]
---

Here to find an easy way to install OpenCV,
and don't care much about the specifics?

Do this:

    git clone git@github.com:krystofl/install-opencv.git
    cd install-opencv
    ./install_opencv.py

[Here's the github repo for the installation script.](https://github.com/krystofl/install-opencv "Github")


## Why I Wrote This Script and Blog Post

OpenCV is a pain in the ass to install.

The [official instructions](https://docs.opencv.org/trunk/d7/d9f/tutorial_linux_install.html)
are decent if you know where to find them,
have been doing Linux development for a while,
and feel like spending time on the installation process.
For everyone else, they're frustrating.
They're hard to find, they have a whole bunch of steps,
substeps, ambiguities, and decisions that are left up to user.

That's why so many others are writing their own sets of instructions.

Googling ["install opencv"](https://www.google.com/search?q=install+opencv)
yields about 468,000 results as of this writing.
The top 4 results have between 4-9 steps (often with substeps),
and they are long.

Most of the time when I'm installing a library,
I'm thinking about what I want to use it for.
What sweet application for computer vision have I thought up now?
That's where I want my mental energy to go - not on figuring out
which installation flags I should set and how.

I was recently installing OpenCV on three separate computes within
a span of a few weeks and grew frustrated with the process.


## About This Script

My motivation was to write something that would be really easy
and helpful most of the time for most people.

The instructions to use it are literally one step: **run the script**.

This should install OpenCV (C++ and Python):

    git clone git@github.com:krystofl/install-opencv.git
    cd install-opencv
    ./install_opencv.py

[The github repository is here.](https://github.com/krystofl/install-opencv)

The repo has a README, which you should probably skim.

By default, the script installs opencv's prerequisites,
so you should be able to run it on a fresh OS install and
*it should just work*. It runs in python 3.

To see the installation options, run `./install_opencv.py --help`.

One flag that may be helpful is `-p`, which tells the script NOT to
install prerequisities.

Also helpful is `-b` to tell the script to load build
and installation flags for cmake from a JSON file.
What are all of the available flags? Who knows?
The [official installation instructions](https://docs.opencv.org/trunk/d7/d9f/tutorial_linux_install.html)
are helpful, but not exhaustively so.



## When NOT to Use This Script

Please note that this script is something I originally
wrote for myself for *my own use case*.
I think it will be helpful to others, so I've decided to share it.
However, the script is not thoroughly tested, so use your own judgement.
It seems to work fine on Ubuntu 16.04; I haven't tested it on other configurations.

I can think of a number scenarios for when **not** to use this script:
- production systems
- if you need or want virtual environments (not a bad idea)
- [if you want to run multiple versions of opencv on the same system]({{site.url}}/2014/03/09/how-to-have-multiple-versions-of-the-same-library-side-by-side/)


## Final Notes

The script currently does not install
[opencv_contrib](https://github.com/opencv/opencv_contrib "OpenCV Extra Modules Github")
(OpenCV's "extra modules"). I haven't needed them.
I will probably add an option to install these to this script...
the next time I need those modules. If you need them, why not fork my repo
and add it?

If this post has helped you, or if you have suggestions on how to improve it,
please let me know by commenting below.
Thanks!
