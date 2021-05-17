---
layout: post
title: Building a Second Brain
description: "Stop trying to remember things; start making connections."
tags: [Books, Opinion]
photos_dir: "2021-05-16-building-a-second-brain"
banner_image: krystofs-roam-graph-cropped.png
---

One of the most powerful takeaways I got from reading David Allen's excellent [Getting Things Done: The Art of Stress-Free Productivity](https://www.goodreads.com/book/show/1633.Getting_Things_Done) is to ***not*** rely on my brain to remember things that need to get done.

The trick is to instead rely on a system that is external to your brain and to fully commit to using it - to capture everything that needs to get done and any pertinent notes about it outside of the brain. This frees up brain cycles from trying to memorize long lists of things (which a piece of paper or software can do a lot better than you) and lets you instead focus on creating value. The effect of this on reducing stress is immediate and profound.

Allen first published the book in 2002, and his suggestions were decidedly old-school and paper-based. These days there is no shortage of digital tools to keep TODO lists - Asana and Trello and about a million others.

But while all these tools are reasonably good the core job of keeping a list of things to do and letting you check them off, they also kind of suck in capturing complex ideas and more generally supporting the job of figuring out how to do these things when they are nontrivial and the path to getting them done is not clear at the beginning - which one might argue is the case for most interesting, challenging, and valuable work.

What are the features and qualities of tools to do that?

<!--more-->


# Connected Thinking & Where Good Ideas Come From

Steven Johnson's [Where Good Ideas Come From](https://krystof.litomisky.com/2020/06/07/where-good-ideas-come-from-book-notes/) is a really excellent book on "the natural history of of innovation", which I recommend very highly. Quoting my notes on the book:

> One good way to nurture hunches is to write them down. This became very popular during the enlightenment in the form the “[commonplace book](https://en.wikipedia.org/wiki/Commonplace_book)” - a journal where one would write down ideas, hunches, passages of books and so on. The book would not be strongly structured in order to encourage at-first unrelated hunches to live side by side, such that they may interact and evolve - but it should have an index, so that passages about a particular topic could readily be found.

What you need is a place to record all your hunches and your ideas, but also link them to each other and to relevant topics, and to be able to surface them later, both actively and serendipitously.

One well-developed method to do this is [Zettelkasten](https://en.wikipedia.org/wiki/Zettelkasten), originally developed in the 16th century by Conrad Gessner:

> A zettelkasten consists of many individual notes with ideas and other short pieces of information that are taken down as they occur or are acquired. The notes are numbered hierarchically, so that new notes may be inserted at the appropriate place, and contain metadata to allow the note-taker to associate notes with each other.

Zettelkasten is not the only game in town - see the [Wikipedia article on Personal Knowledge Management](https://en.wikipedia.org/wiki/Personal_knowledge_management) - but the core principles tend to be the same.

So what are some modern software tools that support connected thinking?



# Building a Second Brain

There's been an explosion of software tools to support building a second brain - see the list in the <a href="#references">References section below</a>.

I've had many miscellaneous note systems, from Evernote to Google Keep and others in between, but didn't love any of them.

When I decided to get more organized, I started off with keeping a large number of Google Docs, one for each large project, with links between them, as well as an "Index" Doc that linked to all the others. This approach went surprisingly far, but the cross-referencing and discovery were very poor.

I tried setting up my own Wiki using [MediaWiki](https://www.mediawiki.org/wiki/MediaWiki), the open-source software that powers Wikipedia. I found it time-consuming and slow to edit, and too rigidly structured to quickly record all those hunches as they come.

I setup a [TiddlyWiki](https://tiddlywiki.com/) with the [Stroll plugin](https://tiddlywiki.com/), and this felt like a breakthrough. In particular, the automatic creation of backlinks (when I link from Elon Musk's page to SpaceX, a link to Elon Musk automatically shows up in the references section of the SpaceX page) greatly helped me connect things, and the super easy creation of new pages (literally just type the name of the page in square brackets) were gamechangers.

It still wasn't quite there, though: I switch computers frequently (if nothing else, between there are some things that only work properly under Linux, and others that only work properly under Windows), and TiddlyWiki didn't have a great way to sync information between computers. I tried Dropbox and thought about git, but both felt clunky.

I looked around at other options and decided to give [Roam Research](https://roamresearch.com/) a try.



# Roam Research

At $15 per month, Roam isn't cheap, and I honestly didn't think I'd be willing to pay for it... but a year later here I still am with an active subscription.

Roam bills itself as _"a note-taking tool for networked thought. As easy to use as a document. As powerful as a graph database. Roam helps you organize your research for the long haul."_

Here's my graph, with daily journal entries hidden and the draft of this post and connected pages highlighted:

<center>
{% include post_image_full.html
   filename="krystofs-roam-graph.png"
   title="Krystof's Roam Graph"
   caption="Krystof's Roam Graph" %}
</center>

For an introduction to Roam, check out the [Welcome to Roam](https://roamresearch.com/#/app/help/page/80uPAx8m-) graph; it includes intro videos, among other things. For the insights and purposes behind Roam and connected thinking more generally, I highly recommend reading the [Roam White Paper](https://roamresearch.com/#/app/help/page/dZ72V0Ig6).

My favorite thing about Roam is probably how easy it is to create pages and link between them. For example, to link to a page, just type its name in double square brackets or the `#` symbol. Roam will autocomplete for you, and if the page doesn't exist, it gets created, just like that. No "create new page" dialogue option needed.

I'm also a fan of the automatically-created Daily Notes page - each day starts with a blank page. As I go through the day, I take quick notes there and quickly link them to existing pages and ideas.

Here's one workflow that has been a real game-changer for me. I read most of my books on a Kindle, and I love the easy ability to quickly highlight sections and take notes. When I finish a book, I import all of my notes from Kindle into my Roam graph, using [this script I wrote](https://github.com/krystofl/kindle-notes-to-md). I then go through the notes again in Roam and rewrite them into my own Book Notes, [some of which I then publish here](https://krystof.litomisky.com/tags/index.html#Books).

Because of how easy it is to link ideas together, I can "pre-create" links between the book notes and individual ideas and concepts right as I read the book in Kindle. For example, if I read a great section on meditation that I want to save for future reference, I can just add a note with `#Meditation` in Kindle - and when I import those notes into Roam, the bidirectional link between the book notes and my Meditation page will automatically be created.

This whole process around books has greatly improved my recall of the books I read.



# Room for Roam Improvement

It's not all easy-peasy though. Because the structure of your graph database is entirely up to you, there are many different ways to set it up, and it's easy to end up with a graph that is all over the place.

Bringing this back to _Getting Things Done_, one thing that I find challenging is keeping track of things I need to do. I am convinced that tasks and notes need to live side-by-side, but I have not found a simple and reliable way to get Roam to answer this: "Show me the list of everything I need to do, sorted by due date, and let me filter by project."

I can look at the links to the `TODO` page and apply filters there, but I find it much less clear than, say, the view of my tasks in Asana. I also can't create recurring tasks in Roam, which is another thing Asana does well. On the other hand, Asana sucks for taking notes. And so, sadly, for now I keep track of tasks with deadlines in Asana and everything else in Roam.

I also really miss the Outline feature that works nicely in Google Docs - with a single click I can instantly go to any section of my document. This should super easy to implement in Roam - yet it isn't there.

Another thing Google Docs does well is comments - I can easily share a doc with others, and they can comment directly on a specific paragraph or even sentence. I do not see an easy way to get feedback like this with Roam.

The load times for Roam can be horrendous. Worse, the centroid of the spinning part of the astrolabe in the loading animation isn't aligned properly with the stationary part, so the damn thing looks like it wobbles. The OCD perfectionist in me shivers every time I see the thing... which is often. Can I please fix it for you, Conor, if no one else will?

As of right now there is also no Roam mobile app, and the web app works only so-so on mobile. I usually take notes in Google Keep on the go and then transfer them to Roam on my computer as appropriate.

Roam isn't officially in Beta as far as I can tell, and I'm already paying for it, but it does still feel like Beta software.



# Final Thoughts

We all generate and process more information than ever, and the trend is accelerating. It does not seem reasonable to try to keep all of that information in our heads - evolution moves on much longer timelines than information technology. In any case, those who figure out good ways to store, retrieve, connect, and otherwise interact with knowledge outside of the limitations of their biological brains will have a huge advantage over those who do not.

And so I am trying to build a second brain outside of my biological body. Roam has so far been my favorite way to capture it. Though I think there is much room for improvement, I've found Roam to be super helpful and am a huge fan.

There are many other tools and approaches to the task of building a second brain - check out the links below. It seems like Roam pioneered (or popularized, or showed the power of?) backlinks, and there has been an explosion of software that builds on that idea. Some of the many options are listed below.

How do you keep track of what you know?


<a name="references" />
# Links & References

Personal knowledge management approaches:
- [Personal Knowledge Management on Wikipedia](https://en.wikipedia.org/wiki/Personal_knowledge_management)
- [Zettelkasten on Wikipedia](https://en.wikipedia.org/wiki/Zettelkasten);  [Zettelkasten.de (in English)](https://zettelkasten.de/posts/overview/)
- [The PARA Method: A Universal System for Organizing Digital Information](https://fortelabs.co/blog/para/) from Thiago Forte


Software for connected thinking & personal knowledge management:

- [Roam Research](https://roamresearch.com/) - _"As easy to use as a document. As powerful as a graph database. Roam helps you organize your research for the long haul."_
- [Athens Research](https://github.com/athensresearch/athens) - aims to be open-source Roam and then some. Fun story: Roam was rejected by Y Combinator. Jeff Tang applied to work at Roam, and got turned down. Jeff Tang then started Athens, applied to Y Combinator with it, and got in.
- [Tiddlywiki](https://tiddlywiki.com) with the [Stroll plugin](https://giffmex.org/stroll/stroll.html) (free)
- [Zettlr](https://www.zettlr.com/) - a powerful markdown editor
- [Obsidian](https://obsidian.md/) - _"a powerful knowledge base that works on top of a local folder of plain text Markdown files"_ (free; phone apps in private beta)
- [Coda](https://coda.io/welcome) - _"a new doc that brings all of your words and data into one flexible surface."_
- [Logseq](https://logseq.com/) - _"local-only, non-linear, outliner notebook for organizing and sharing your personal knowledge base"_. Supports both markdown and Emacs Org Mode.
- [Linkist](https://github.com/gladed/linkist) - an extension for Visual Studio Code and [Atom](https://atom.io/packages/linkist) to create persistent links between markdown documents.
- [Dendron](https://www.dendron.so/) - Visual Studio Code extension
- [Emacs Org mode](https://orgmode.org/) - because you can do anything with emacs
- [Workflowy](https://workflowy.com) - _"Workflowy replaces your notebooks, stickies and bloated apps with a simple, smooth digital notebook that makes it easy to get organized and be productive."_
- [Emvi](https://emvi.com/) - team knowledge base. [Emvi blog post on Zettelkasten](https://emvi.com/blog/luhmanns-zettelkasten-a-productivity-tool-that-works-like-your-brain-N9Gd2G4aPv)
- [Notion](https://www.notion.so) - _"One tool for your whole team. Write, plan, and get organized."_
- [Evernote](https://evernote.com/) - doesn't really do connected thinking as far as I can tell, but it's the old-school 800-pound gorilla in note-taking, so I figured I'd include it.
- [Comparison of Note-Taking Software on Wikipedia](https://en.wikipedia.org/wiki/Comparison_of_note-taking_software)
- [A very extensive list of networked note-taking apps](https://www.notion.so/Artificial-Brain-Networked-notebook-app-a131b468fc6f43218fb8105430304709)

And a great example: [Nikita Voloboev's Everything I Know Wiki](https://wiki.nikitavoloboev.xyz/)
