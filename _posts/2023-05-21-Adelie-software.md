---
layout: post
title: "Project Adelie - Modern Software for Modern Industry"
description: "How we applied the best practices of modern software engineering at Ecogate to develop a state of the art industrial controller."
tags: [Software, Linux]
---

Two weeks ago,
[the team at Ecogate unveiled the 2023 greenBOX NXT](https://www.ecogate.com/post/2023-greenbox-nxt-the-future-of-industrial-ventilation-control-systems),
the new state of the art for control of industrial dust, mist, and fume collection systems.

![2023 greenBOX NXT from Ecogate](https://static.wixstatic.com/media/25bde7_7ccc6a7414cf436d9497d4bbc541b982~mv2.webp)

> Boasting powerful industrial hardware and a modern software architecture, this unit can effortlessly handle industrial ventilation systems throughout an entire factory. With improved measurements of ventilation values, pressures, air velocities, and air volume are measured and regulated.

This week, [we shared more about the software architecture for the new controller](https://www.ecogate.com/post/modern-dust-fume-mist-collection-deserves-modern-software), which I started building back in 2020. I'm particularly proud of how this turned out.

We started with a goal to build nothing less than the greatest industrial dust collection controller the world has ever seen, and to build it with a software stack that the most successful tech companies in the world would be proud of. In this we have succeeded.

Many of the guiding principles come from
[Google's Sate of DevOps Report](https://cloud.google.com/devops), which systematically analyzes and quantifies software development best practices.
[I wrote about some of those findings back in 2020](/2020/04/06/accelerate-book-notes/).

<!--more-->

The greenBOX runs Ubuntu Linux, with operating system images built from configuration files (following the best practice of _everything_ as code) by
[mkosi from systemd](/2020/09/08/mkosi-for-ubuntu/).

We use [Mender](https://mender.io/) for secure, image-based over-the-air updates. Inter-process communication is handled by [ZeroMQ](https://zeromq.org/). Control software is written in modern C++, with some supporting modules written in Python. The user interface is a React web-app. The whole stack is containerized and orchestrated by Docker Compose.

In summary, it's a great, modern stack, built with the best practices of modern software engineering in mind.

For more information,
[check out the original blog post from Ecogate](https://www.ecogate.com/post/modern-dust-fume-mist-collection-deserves-modern-software).
