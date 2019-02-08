---
title: "JBOSS Cluster Setup"
categories:
  - Markdown
tags:
  - servers
  - JBOSS
  - middleware
  - plumbing
last_modified_at: 2019-01-28T12:25:10-05:00
---

##### Work in progress blog post


### JBOSS Cluster Setup

As per the documentation available for JBOSS on Red Hat's [website](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/7.0/html/getting_started_guide/introduction)

`"Red Hat JBoss Enterprise Application Platform 7 (JBoss EAP) is a middleware platform 
built on open standards and compliant with the Java Enterprise Edition 7 specification."`

Think of it as the the plumbing between your application and the server on which it is hosted.

`"JBoss EAP provides two operating modes for JBoss EAP instances: standalone server or 
managed domain. The standalone server operating mode represents running JBoss EAP as a
single server instance. The managed domain operating mode allows for the management of
multiple JBoss EAP instances from a single control point. "`

`"In addition, JBoss EAP includes APIs and development frameworks for quickly
developing secure and scalable Java EE applications. "`

In other words, you deploy a website on a web server, similarly, you deploy a Java Web application
on a application server such as JBOSS.

In this blog post, we will setup the application server JBOSS cluster with 2 nodes and deploy a demo application on top of it.
For the two nodes of JBOSS you can use any of the machines available to you. I have done this using Vagrant as well as Docker.
For the scope of this blog post I will be using Docker. If you have a powerful machine, Vagrant will be easy to use as well.

Here is a simple architecture diagram of a 2 node cluster setup.

<img src="/assets/images/jboss-cluster-architecture.png" alt="JBOSS cluster architecture"/>

In the architecture diagram above I am using the terms `Leader` for the main node and `follower` for the sub domain node.
Consider this similar to master and slave terminologies, I am avoiding those terminologies because of [this](https://bugs.python.org/issue34605)

**Step I : Prepare the machines/Containers**


<img src="/assets/images/step-1-docker-containers-init.png" alt="Setting up containers"/>
