---
layout: post
title: "Programatically Creating Ubuntu Images with systemd's mkosi"
description: "Programatically Creating Ubuntu Images with systemd's mkosi"
tags: [Software, Linux]
---

[mkosi](http://0pointer.net/blog/mkosi-a-tool-for-generating-os-images.html)
is a great tool to programmatically create reproducible images of operating systems. This has a lot of applications in IoT, security, automated testing, managing servers etc. I like it a lot.

mkosi can make images of Fedora, Debian, Ubuntu, ArchLinux, and OpenSuse. There are some differences between those distributions, though, and probably because of that some things are supposed to work... don't, for some distros.

This post is about the quirks of making Ubuntu images with mkosi. In some cases, the documentation for how to make mkosi do something for an Ubuntu images is just plain wrong (though presumably it works for other distros). In other cases, I had a hard time finding information. Hopefully this post helps you to get mkosi working for Ubuntu images in less time than it took me.

<!--more-->


# mkosi - A Very Brief Introduction

Probably the best introduction to mkosi is
[this blog post](http://0pointer.net/blog/mkosi-a-tool-for-generating-os-images.html)
from [Lennart Poettering](https://en.wikipedia.org/wiki/Lennart_Poettering), who created systemd and mkosi. If you haven't read it yet, please do so now; I won't repeat most of it here, and this blog post only touches on a subset of everything mkosi can do.

From there is this great description of mkosi:
> mkosi is definitely a tool with a focus on developer's needs for
building OS images, for testing and debugging, but also for generating
production images with cryptographic protection... mkosi will put together the image with development headers and tools, compile your code in it, run your test suite, then throw away the image again, and build a new one, this time
without development headers and tools, and install your build artifacts in it. This final image is then "production-ready", and only contains your built program and the minimal set of packages you configured otherwise.

**Resources:**
- [mkosi introductory blog post](http://0pointer.net/blog/mkosi-a-tool-for-generating-os-images.html)
- [mkosi repository](https://github.com/systemd/mkosi)
- [mkosi man page](https://github.com/systemd/mkosi/blob/master/mkosi.md)

It should also be noted that for making Ubuntu images, mkosi uses `debootstrap` under the hood.



# Quickstart Github Repo

I made a
[companion Github repository](https://github.com/krystofl/mkosi-for-ubuntu)
for this post in the interest of making this all easy to try out. I suggest that you clone the repository now.

We'll be using the following files/directories:
- **`mkosi.default`**: The main configuration file where you
configure what kind of image you want, which distribution, which
packages and so on.
- **`mkosi.postinst`**: This executable script is invoked inside the image
 adjust the image as it likes at a very late point in the image
 preparation. If ``mkosi.build`` exists, i.e. the dual-phased
 development build process used, then this script will be invoked
 twice: once inside the build image and once inside the final
 image. The first parameter passed to the script clarifies which phase
 it is run in. The script runs in the image as the root user.
- **`mkosi.extra`**: If this directory exists, then mkosi will copy
 everything inside it into the images built. You can place arbitrary
 directory hierarchies in here, and they'll be copied over whatever is
 already in the image, after it was put together by the distribution's
 package manager. This is the best way to drop additional static files
 into the image, or override distribution-supplied ones.

To install mkosi, run `sudo apt install mkosi`.

You can then create the image by running `sudo mkosi` - it should just work.

From here on, I'll focus just on the quirks of using mkosi to make specifically Ubuntu images.



# Installing The Latest Package Versions

Let's say we want an Ubuntu 20.04 aka "focal" image. To do that, we'd specify the following in `mkosi.default`:

    [Distribution]
    Distribution=ubuntu
    # 20.04 = focal
    Release=focal

This would install the package versions that focal was released with. In most cases, this is NOT what you want: you generally want the latest stable versions of the packages for that distribution. This would ensure that you get any security updates, for example.

To do that, first tell mkosi to give its scripts access to the network by setting this in `mkosi.default`:

    [Packages]
    # let mkosi.postinst access the internet
    # (needed because we are updating and installing packages there)
    WithNetwork=yes

Then install updates from `mkosi.postinst`:

    # don't ask me any questions, apt
    export DEBIAN_FRONTEND=noninteractive

    # add package repository for updates to sources list
    add-apt-repository "deb http://archive.ubuntu.com/ubuntu focal-updates main universe"

    # update package lists
    apt-get -y update

    # install updates
    apt-get -y upgrade

After this, your image will have the latest stable versions of whatever packages you set to be installed in `mkosi.default`.

There is a caveat here: by doing this, your images will not be strictly the same every time you run the script - the final state will depend on what package versions were released at the time you ran the script. Most of the time this is what you want.



# Adding Package Repositories

If you want to install packages that are not in the default Ubuntu package repositories, unfortunately the `Repositories=` flag will NOT work as specified in the documentation. The flag expects a URL... and Ubuntu packages don't quite work that way.

The easiest way I've found to accomplish this is to again use `mkosi.postinst`.

For example, here's how to install Docker, using
[the official instructions](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository):

    # get the docker GPG key
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -

    # add the docker package repository
    add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) \
      stable"

    # update package lists and install docker
    apt-get -y update
    apt-get -y install docker-ce docker-ce-cli containerd.io



# Docker Caveats

_Thanks to reader MarekLi for contributing to this section!_

Docker is great, but getting it to work nicely with mkosi can be tricky. In particular, to use it in `mkosi.postinst`, you have to manually start the `containerd` and `dockerd` deamons like so:

```
echo -e "\n\nStarting containerd and dockerd...\n"

# Start containerd
/usr/bin/containerd &
CONTAINERD_PID=$!
sleep 2

# Start dockerd
/usr/bin/dockerd -H unix:///var/run/docker.sock --containerd=/run/containerd/containerd.sock --iptables=false --bridge=none &
DOCKERD_PID=$!
sleep 2

# Interact with the docker daemon as needed
# docker load -i $tarfile etc


# Kill dockerd and containerd
echo -e "\n\nStoping dockerd and containerd...\n"
kill $DOCKERD_PID
sleep 2
kill $CONTAINERD_PID
```

As an alternative, you could use a script (that runs on the machine from which you invoke mkosi) that downloads the needed containers as tarballs and saves them in a folder under `mkosi.extra`, so that they get included in the final image.

The commands to do that are

    docker pull IMAGE:TAG
    docker save -o mkosi.extra/IMAGE.tar IMAGE:TAG

Then, when the image actually boots for the first time, you can load the images from the tarballs like so:

    docker load -i IMAGE.tar

One advantage of doing it this way, rather than just having the image pull the containers directly from the internet, is that this process works even if the machine running the image is not connected to the internet, which may indeed be the case for certain IoT applications.



# Final Notes

This post only touches on a subset of what mkosi can do, and specifically focuses on things where using mkosi for Ubuntu images is tricky.
[Lennart Poettering's blog post](http://0pointer.net/blog/mkosi-a-tool-for-generating-os-images.html) remains the best introduction to mkosi, as far as I can tell.

I hope this post helps you programmatically make reproducible Ubuntu system images.

Happy hacking!
