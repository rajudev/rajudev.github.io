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
**_NOTE: This post is a work in progress_**

### Overview
I have been using git for a while now in my workflow. I find my self proficient
enough with git to perform most of the usual tasks involved in the version control
management systems. 

But recently I decided to dive deep and finish one of the tasks in my bucket list, 
i.e. mastering git in depth.
I planned to do this by reading the **_Pro Git_** book written by **_Scott Chacon_** & 
**_Ben Straub_**. 
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

## 3. Apart from the usual **_git://_** and **_https://_** protocols git can also clone a repo from another computer.
Git has a number of different transfer protocols you can use. Most people 
use **_https://_**  or **_git://_** , but you can also clone repos from another machine. 

```sh
$ git clone user@server:path/to/repo.git
```
This uses the SSH transfer protocol.

## 4. Short Git status
While the git status output is pretty comprehensive, it’s also quite wordy.
Git also has a short status flag so you can see your changes in a more compact way. 
If you run **_git status -s_** or 
**_git status --short_** you get a far more simplified output from the command:
```sh
$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
```
New files that aren’t tracked have a **_??_** next to them, new files that have been 
added to the staging area have an **_A_**, modified files have an **_M_** and so on.

## 5. Awesome **_git log_**
By default, with no arguments, **_git log_** lists the commits made in that repository
in reverse chronological order. A huge number and variety of options to the git log
command are available to show you exactly what you’re looking for. 
Here, I'll show some of the most useful ones.
  1. **_git log --patch_** or **_git log -p_**
  Shows the difference (the patch output) introduced in each commit.
  You can also limit the number of log entries to be displayed by supplying
  the number in front of the command, such as **_git log --patch -2**
  ```sh
  $ git log -p -2
  commit ca82a6dff817ec66f44342007202690a93763949
  Author: Scott Chacon <schacon@gee-mail.com>
  Date:   Mon Mar 17 21:52:11 2008 -0700

      changed the version number

  diff --git a/Rakefile b/Rakefile
  index a874b73..8f94139 100644
  --- a/Rakefile
  +++ b/Rakefile
  @@ -5,7 +5,7 @@ require 'rake/gempackagetask'
  spec = Gem::Specification.new do |s|
      s.platform  =   Gem::Platform::RUBY
      s.name      =   "simplegit"
  -    s.version   =   "0.1.0"
  +    s.version   =   "0.1.1"
      s.author    =   "Scott Chacon"
      s.email     =   "schacon@gee-mail.com"
      s.summary   =   "A simple gem for using Git in Ruby code."

  commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
  Author: Scott Chacon <schacon@gee-mail.com>
  Date:   Sat Mar 15 16:40:33 2008 -0700

      removed unnecessary test

  diff --git a/lib/simplegit.rb b/lib/simplegit.rb
  index a0a60ae..47c6340 100644
  --- a/lib/simplegit.rb
  +++ b/lib/simplegit.rb
  @@ -18,8 +18,3 @@ class SimpleGit
      end

  end
  -
  -if $0 == __FILE__
  -  git = SimpleGit.new
  -  puts git.show
  -end
  ```
  2. **_git log --stat_**
   If you want to see some abbreviated stats for each commit, you can use the **_--stat_** option:
   ```sh
   $ git log --stat
   commit ca82a6dff817ec66f44342007202690a93763949

   Author: Scott Chacon <schacon@gee-mail.com>
   Date:   Mon Mar 17 21:52:11 2008 -0700

       changed the version number

   Rakefile | 2 +-
   1 file changed, 1 insertion(+), 1 deletion(-)

   commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
   Author: Scott Chacon <schacon@gee-mail.com>
   Date:   Sat Mar 15 16:40:33 2008 -0700

       removed unnecessary test

   lib/simplegit.rb | 5 -----
   1 file changed, 5 deletions(-)

   commit a11bef06a3f659402fe7563abf99ad00de2209e6
   Author: Scott Chacon <schacon@gee-mail.com>
   Date:   Sat Mar 15 10:31:28 2008 -0700

       first commit

   README           |  6 ++++++
   Rakefile         | 23 +++++++++++++++++++++++
   lib/simplegit.rb | 25 +++++++++++++++++++++++++
   3 files changed, 54 insertions(+)
   ```

## 6. 

## 7. 

## 8. 
