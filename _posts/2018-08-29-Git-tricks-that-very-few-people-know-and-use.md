---
title: "Awesome Git facts and tricks: Notes from the Pro Git book"
categories:
  - Markdown
tags:
  - git
  - CLI
  - terminal
  - version-control
  - VCS
  - awesome
last_modified_at: 2018-08-29T12:25:10-05:00
---
`NOTE: This post is a work in progress`

### Overview
I have been using git for a while now in my workflow. I find my self proficient
enough with git to perform most of the usual tasks involved in the version control
management systems. 

But recently I decided to dive deep and finish one of the tasks in my bucket list, 
i.e mastering git in depth.
I planned to do this by reading the *Pro Git* book written by *Scott Chacon* & 
*Ben Straub*. 
The book is available to read online at [git-scm.com](https://git-scm.com/book/en/v2)

In this blog post I will be writing the facts and tricks I learned from the book.
Following are my discoveries.

## 1. The checksum that we see in git commits is 40 hexadecimal characters
The mechanism that Git uses for this checksumming is called a SHA-1 hash. 
This is a 40-character string composed of hexadecimal characters (0–9 and a–f) 
and calculated based on the contents of a file or directory structure in Git. 
A SHA-1 hash looks something like this:

```
24b9da6552252987aa493b52f8696cd6d3b00373
```
You will see these hash values all over the place in Git because it uses them so 
much. In fact, Git stores everything in its database not by file name but by 
the hash value of its contents.

## 2. You can clone a git repository under a different folder name

If you want to clone the git repository into a directory named something other 
than what the repository name uses, you can specify the new directory name as
an additional argument:

Syntax
```sh
$ git clone <base-URL/repository-name> new-folder-name
```

Example
```sh
$ git clone https://github.com/libgit2/libgit2 mylibgit
```

## 3. Apart from the usual *git://* and *https://* protocols git can also clone a repo from another computer.
Git has a number of different transfer protocols you can use. Most people 
use *https://*  or *git://* , but you can also clone repos from another machine. 

```sh
$ git clone user@server:path/to/repo.git
```
This uses the SSH transfer protocol.

## 4. Short Git status
While the git status output is pretty comprehensive, it’s also quite wordy.
Git also has a short status flag so you can see your changes in a more compact way. 
If you run *git status -s* or *git status --short* you get a far more simplified output from the command:
```sh
$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
```
New files that aren’t tracked have a *??** next to them, new files that have been 
added to the staging area have an *A*, modified files have an *M* and so on.

## 5. 

## 6. 

## 7. 

## 8. 
