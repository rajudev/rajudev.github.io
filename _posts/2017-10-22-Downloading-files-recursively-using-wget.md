---
title: "Using Regular Expressions while Downloading files with wget"
categories:
  - Markdown
tags:
  - shell
  - title
  - customization
  - CLI
  - terminal
  - bash
  - wget
  - download
  - debconf
last_modified_at: 2017-10-22T12:25:10-05:00
---

### Overview

I encountered this interesting situation the other day. I wanted to download multiple files from a website.
Particularly all the Videos of all Talks from DebConf 17, which happened this year in Montreal, Canada. (I dreamed of going there sometime back)

So Headed over to [Debconf17 Website ](https://debconf17.debconf.org/) and got to the [Videos](http://meetings-archive.debian.net/pub/debian-meetings/2017/debconf17/) page.

<img src="/assets/images/Selection_023.png" alt="List of "/>

So I wanted to download all the videos from this web page, but not manually. All at once. We can easily do that using wget.

```
wget -rcv http://meetings-archive.debian.net/pub/debian-meetings/2017/debconf17/
```
-r --> download all files and folders recursively.
-c --> continue any broken downloads. If the connection breaks, continue downloading a previous file, instead of re-downloading it.
-v Be verbose and tell us what you are doing in detail.


This command will download all the videos on the webpage, including the sub folder of `lq` as we have given the `-r` parameter to wget, which tells to download all files recursively.


Now as you can see that each video is available there in two qualities. Now I don't want to download the two Similar videos in different qualitites. Also I don't want to download the `lq` folder which contains the loas quality videos.
This is where using regular expressions aka, `regex` in wget comes in to play.

So lets modify our command to download only the videos we want and exclude the ones that we don't want.

```
 wget -rcv --accept-regex 'vp8' --reject-regex 'lq' http://meetings-archive.debian.net/pub/debian-meetings/2017/debconf17/
```

We only want the videos which has `vp8` in its name/url, which are higher quality. We want to exclude the videos which has `lq` in there url so that we exclude the lq folder.
And when we execute this, we only get the videos that we wanted.
Now you can take this example and download the videos that you want, be of debconf,defcon etc.
