---
layout: post
title: "Why You Should Use Class Enums in C++"
description: ""
tags: [C++, Software]
---

*This post was originally published on
<a href="http://code.litomisky.com/2014/04/17/why-you-should-use-class-enums-in-c/"
   target="_blank" title="Admiral Ackbar's Code Emporium">
   Admiral Ackbar's Code Emporium
</a>.*


This is a brief post about what class enums are in C++, and why you should use them.

## The Problem: Enums Pollute Global Scope

Here's a conflict you might get when using enums:

{% highlight cpp %}

enum computer_state { ON = 0 , OFF, STANDBY };
enum disco_ball     { OFF = 0, ON };

int state = ON; //CONFLICT - this won't compile

{% endhighlight %}

<!--more-->


## Old School Solutions

Here are two solutions for the above conflict:

{% highlight cpp %}
enum computer_state { COMPUTER_STATE_ON = 0, COMPUTER_STATE_OFF, COMPUTER_STATE_STANDBY };
enum disco_ball     { DISCO_BALL_OFF = 0, DISCO_BALL_ON };

int state = DISCO_BALL_ON;
{% endhighlight %}


The above works, but it is messy, and requires you to be dilligent in naming your values consistently. Here's a solution with a cleaner result:

{% highlight cpp %}
namespace computer_state { enum type { ON  = 0, OFF, STANDBY } ; }
namespace disco_ball     { enum type { OFF = 0, ON }; }

int state = disco_ball::ON;
{% endhighlight %}

The result above is much cleaner, but the syntax to define it is a little clunky.

## The C++11 Solution: Class Enums

This is why C++11 defined the class enum. Here's how to use it:

{% highlight cpp %}
enum class computer_state { ON  = 0, OFF, STANDBY };
enum class disco_ball     { OFF = 0, ON };

//the compiler won't allow implicit type conversion here - we need to cast the value to an int
int state = static_cast<int>(disco_ball::ON);
{% endhighlight %}

Here we get the same clean access, and the syntax to define the enums is nice and clean as well. That's why you should be using class enums wherever you've been using enums in the past!
