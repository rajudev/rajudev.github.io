---
title: "Building a deb package with Gitlab CI"
categories:
  - Markdown
tags:
  - linux
  - Debian
  - gitlab
  - CI/CD
  - packaging
last_modified_at: 2018-01-24T12:25:10-05:00
---

## Note: This post is a Work in progress. 

To-do: Building any Debian package using gitlab-ci and in the process learn how gitlab-ci works.

Pre-Requisites: basic knowledge of git, software packaging in general and Debian packaging in particular, 
and some knowledge of docker containers. 

Continuos integration, delivery and deployment is designed to help speed up the development and testing process of software. While I was learning to use Jenkins to run build Jobs for Hamara Linux, I came across Gitlab CI, the CI integrated into the interface of gitlab.com as well as which can be configured on any instance of Gitlab's community edition. 

In this post we will learn a how to of using Gitlab-ci and building Debian packages in the process.

Building Debian Packages is just a use case that I am going to follow, while you can modify the process
suitable to any of your software related use cases, like deploying a Python/Ruby/JS App, building rpm packages or anything else. 

Gitlab CI is readily available for use on gitlab.com. If you are using any other gitlab-ce server, then you have to setup a Gitlab CI runner yourself on the server side for your instance. I would write a separate blog post on Gitlab CI server side setup, but that is for another blog post. 


For this tutorial I'll assume we are working on gitlab.com. 

Next we need a repository which has the source code for a debian package for example

1.[Hamara Welcome app](https://gitlab.com/rajudev/hamara-welcome)

or some of the popular debianised apps which are present on github.com or anywhere else. 

If the source code for the debian package is not present on gitlab.com, you can create a `New Project` on 
gitlab.com importing the other project using its git url. 

<img src="/assets/images/projectImportonGitlab.png" alt="git project import on gitlab"/>













