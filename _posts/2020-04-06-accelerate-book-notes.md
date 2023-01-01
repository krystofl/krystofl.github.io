---
layout: post
title: "Accelerate: Building and Scaling High-Performing Technology Organizations - Book Notes"
description: ""
tags: [Books, Software, Leadership]
---

***Accelerate: Building and Scaling High-Performing Technology Organizations***<br/>
by Nicole Forsgren, Jez Humble, and Gene Kim<br/>
[Goodreads link](https://www.goodreads.com/book/show/35747076-accelerate)

Software is eating the world - and has been, for quite a while.
No matter the organization or industry, software has a huge impact on the
organization's ability to meet its goals.
If that is the case, then delivering software better would help organizations
meet their goals better.

So how do we deliver software better?

That's the question posed by the authors of
*Accelerate: Building and Scaling High-Performing Technology Organizations*.
To find out, they conducted
research, which they published in annual "State of DevOps" reports.
You can read the
[full 2019 State of DevOps report here](https://services.google.com/fh/files/misc/state-of-devops-2019.pdf).
The data for the 2014-2017 reports was then compiled into this book.

The authors find that the following behaviors positively positively impact software
delivery, which in turn has "a measurable impact on an organization's profitability,
productivity, and market share", as well as "on customer
satisfaction, efficiency, and the ability to achieve organizational goals."



# Continuous Delivery

#### 1. Use version control for all production artifacts
**All production artifacts** - that means not just code (which is the bare minimum),
but also system and application configurations, and scripts for build automation.

<!--more-->

#### 2. Automate your deployment process
#### 3. Implement continuous integration
#### 4. Use trunk-based development models
This means having only a few active branches (fewer than 3),
branches and forks with short lifetimes (e.g. less than a day),
and rarely having "code lock" periods.
#### 5. Implement test automation
#### 6. Support test data management
#### 7. Shift left on security
By this the authors mean having security as an integral part of the entire
development and testing process, as opposed to just having a security review
when the software is late in the development process.
#### 8. Implement continuous delivery


# Architecture

#### 9.  Use a loosely coupled architecture
#### 10. Architect for empowered teams
By this the authors mean letting teams decide what tools they use to
do better at continuous delivery (rather than this being a top-down decision).


# Product and process

#### 11. Gather and implement customer feedback
#### 12. Make the flow of work visible through the value stream
Have high visibility into the flow of work from the business all the way to
customers, including the status of products and features.
#### 13. Work in small batches
The authors suggest slicing work into batches that can be completed in a week
or less.
#### 14. Foster and enable team experimentation
Let teams try out new ideas without requiring any external approval.


# Lean management and monitoring

#### 15. Have a lightweight change approval process
#### 16. Monitor across application and infrastructure to inform business decisions
#### 17. Check system health proactively
Include threshold and rate-of-change warnings.
#### 18. Improve process and manage work with work-in-process (WIP) limits
#### 19. Visualize work to monitor quality and communicate throughout the team


# Cultural

#### 20. Support a generative culture
Generative culture includes "good information flow, high cooperation and trust,
bridging between teams, and conscious inquiry."
[Read more about generative culture here](https://cloud.google.com/solutions/devops/devops-culture-westrum-organizational-culture).
#### 21. Encourage and support learning
#### 22. Support and facilitate collaboration among teams
#### 23. Provide resources and tools that make work meaningful
People's work should be challenging and meaningful, and people should be empowered
to exercise their skills and judgment. Also make sure that people have the
tools and resources they need to do their jobs well.
#### 24. Support or embody transformation leadership
Transformational leadership is comprised of vision, intellectual stimulation,
inspirational communication, supportive leadership, and personal recognition.


# Final Notes

The information is good, but not always presented in an engaging or effective
way. At times the authors seem as interested in their research process as in
the results - which is fine for them, but I think uninteresting for many readers.

The authors' organization, *DORA*, was acquired by Google, and I find that the
information is presented better at
[Google's DevOps Website](https://cloud.google.com/devops).

**3/5** - Good data and insights, but ineffective presentation.
Start with Google's DevOps website (linked above).
