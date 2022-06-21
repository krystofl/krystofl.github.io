---
layout: post
title: "Understanding Sign Language in Video with AI / Machine Learning"
description: "Why don't video-calling platforms provide closed-captions for sign language?"
tags: [Software, Machine Learning, Sign Language]
---

Google Meet now offers real-time closed captions for speakers, and this is very helpful for deaf users using the platform to communicate with hearing and speaking users. In this Google is ahead of the competition - thanks Google!

But that's helpful only in one direction - the deaf person can read the captions to understand the hearing person... but to make themselves understood, the deaf person has to type what they want to say. This is far from ideal.

Could a deaf person sign into the camera and have software create closed captions of what they are signing in real-time?

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/ZoQVTCrRkrw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Yes. I hacked the above demo of software understanding American Sign Language (ASL) together in about a day's worth of work using Google's [MediaPipe Holistic](https://ai.googleblog.com/2020/12/mediapipe-holistic-simultaneous-face.html) framework for face and hand pose prediction and TensorFlow for machine learning.

There are plenty of issues with it: the vocabulary is limited, I taught it all the signs myself (and it might therefore struggle with signing accents), it doesn't use temporal information (and therefore could not tell the difference between some pairs of signs, like "mother" and "grandmother") and so on.

But those are all solvable problems - just a matter of solid engineering work. There is a number of large datasets of labeled training data - [Dr. Bill Vicars's lifeprint](https://www.lifeprint.com/), or [handspeak](https://www.handspeak.com/), or various sources on [giphy](https://giphy.com/search/ASL).

In fact, there's a [lot of demos similar to mine online](https://www.youtube.com/results?search_query=sign+language+recognition+using+machine+learning).

Why hasn't someone built a production version of it? I don't buy the argument that it's a matter of technology anymore. Is it a matter of there not being enough money to be made here? Is it just not considered important enough?

Please ping me if you know any companies building ASL-recognition from video into a commercial product - or if you're thinking about starting one!

*UPDATE: The Economist has published a good overview of the
"[race to teach sign language to computers](https://www.economist.com/science-and-technology/2021/03/06/the-race-to-teach-sign-language-to-computers)" (paywall). The article cites data collection and annotation as a major issue, as well as some technological challenges, including capturing people's facial expressions (I'm calling BS on that - take another look at the video above to see why). On the bright side, there are a number of teams working on the problem... but on the darker side, none of those seem to be at one of the software giants.*
