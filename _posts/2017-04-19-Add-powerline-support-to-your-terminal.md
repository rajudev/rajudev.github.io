---
title: "Add *powerline* support to your terminal"
categories:
  - Markdown
tags:
  - powerline
  - shell
  - title
  - customization
  - CLI
  - terminal
  - bash
last_modified_at: 2017-04-19T12:25:10-05:00
---

**Overview**

Ever wanted to have an amazing looking terminal different than the usual. Well then this post is for you.
I'll be explaining one of the ways to customise your terminal and give it a different look and feel with Powerline

Powerline is a statusline plugin for vim, and provides statuslines and prompts for several other applications, including zsh, bash, tmux, IPython, Awesome, i3 and Qtile.

Using Poweline you can transform your simple terminal which looks like this.

<img src="/assets/images/simpleTerminal.png" alt="simple terminal"/>


Into a nice looking terminal with a fancy prompt like this

<img src="/assets/images/powerlineTerminal.png" alt="Fancy terminal"/>

Instructions to install and configure powerline on your systems

**STEP I**

**Install Powerline**

On Debian or debian based distributions install the following packages.

```
[sudo] apt install powerline fonts-powerline
```

For Fedora and similar distributions install powerline by the following command.

```
[sudo] dnf install powerline powerline-fonts
```


on other linux distributions follow the procedures as per your package managers to install the above pacakges. The package names should be similar or they might be slightly modified.


**STEP II**

**Configure your .bashrc file**

You need to configure your .bashrc file to start powerline whenever you start a new terminal
to edit your .bashrc file.

```
nano ~/.bashrc
```

You can also use any other text editor of your choice.
For shells other than bash, you need to edit there respective `rc` file's.


Now you need to add the following text at the end of your .bashrc file
```
if [ -f `which powerline-daemon` ]; then
   powerline-daemon -q
   POWERLINE_BASH_CONTINUATION=1
   POWERLINE_BASH_SELECT=1
   . /usr/share/powerline/bindings/bash/powerline.sh
fi
```
Notice the path in the lines above of `/usr/share/powerline`. This path can vary between multiple operating systems. Confirm that the file exists at that path in your directory structure. If the path is a different change the path in the above lines accordingly.


now save and exit the file by pressing `Ctrl + o` and `Ctrl + x`


**STEP III**

**Make your changes to come to effect**

Your edits to the .bashrc file are now done, now you need to bring the changes in your .bashrc file to effect.

to do that use the source command like this.

```
source ~/.bashrc
```

for shells other than bash, source there respective `rc` files.


Now you should see that you are getting a nice looking terminal for yourself to use.
