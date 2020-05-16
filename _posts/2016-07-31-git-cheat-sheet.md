---
layout: post
title: "Git Cheat Sheet"
description: ""
tags: [Software]
---


For a while now, I’ve had a gradually-expanding note with various git commands
that I’ve been using as a cheat sheet for git tasks that I do not do often,
but regularly enough to write them down.

I figure putting them here will not only make them (slightly) easier
to get to every time, but may also help other folks out.

So here they are! Keep in mind that this is just a quick
(and intentionally incomplete) cheat sheet –
if you are learning git for the first time,
you’re better off looking elsewhere
[this is a good place to start](https://try.github.io/levels/1/challenges/1).


<!--more-->


## General

Delete a file from the repo (opposite of ‘git add’):

    git rm filename


revert a file to the current committed version:

    git checkout -- filename


cache credentials when using https (seconds):

    git config credential.helper 'cache --timeout=300'


clear cached credentials:

    git credential-cache exit


ignore changes to a versioned file:

    git update-index --assume-unchanged <file>


stop ignoring those changes:

    git update-index --no-assume-unchanged <file>


change commit message of last commit:

    git commit --amend -m "New commit message"



## Branches

See all branches, including remote branches:

    git branch -a


Pull a branch from a remote ("origin" here) and track it
(this is tested and works with git 1.7.2.3 and higher)

    git fetch --all
    git checkout -b branch_name origin/branch_name


push a new local branch to origin:

    git push -u origin branch-name


create a new branch:

    git checkout -b new_branch


merge changes from branch hotfix into master:

    git checkout master
    git merge hotfix


delete the local branch:

    git branch -d hotfix


track a remote branch:

    git branch --set-upstream krystof_plots origin/krystof_plots



## Tags

create a tag and push it to origin:

    git tag -a v1.4 -m 'my version 1.4'
    git push origin --tags


pull tags:

    git pull --tags


find out what tag you’re on:

    git describe --tags



## Forks

Add upstream remote:

    git remote add upstream git@github.com:krystofl/krystof-utils.git


sync a fork (https://help.github.com/articles/syncing-a-fork):

    git fetch upstream
    git checkout master
    git merge upstream/master


Reset a fork to whatever is on upstream:

    git fetch upstream
    git checkout master
    git reset --hard upstream/master
    git push origin master --force


## Submodules

Add a git repo as a submodule:

    git submodule add https://github.com/krystofl/krystof-utils.git


To make the submodule track a the master branch:

open .gitmodules, and add a line to the submodule info:

    branch = master

Remove a submodule (works most of the time):

    git rm path/to/submodule

If the above doesn't work, see
[this StackOverflow answer](https://stackoverflow.com/a/1260982).
