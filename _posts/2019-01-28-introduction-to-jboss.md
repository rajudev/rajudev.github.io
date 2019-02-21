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

### **Step I : Prepare the Machines/Containers**


<img src="/assets/images/step-1-docker-containers-init.png" alt="Setting up containers"/>

We are starting two Docker containers as you can see in the terminal. In the terminal on top we are creating the container for the leader node. 
And in the second container we are starting the container for the follower node. 
Break down of the commands entered are as follows. 

```shell
docker run -it --name="leader" -p 9990:9990 -p 8000:80 centos
```

**docker run** Run a docker container 

**-it** In interactive mode and allocate a psedo tty to it.

**--name="leader"** assign the name leader to it.

**-p 9990:9990 -p 8000:80** expose the external host machines port 9990 to the containers internal 9990 port, similarly for the 8000 port number of the host to the 80 port number of the container. 

**centos** the image name that we have to make the container of, in our case centos.


```shell
docker run -it --name="follower" -p 9991:9990 -p 8001:80 centos
```

In case of the second prompt we are creating the container for the follower that is slave node. Hence the name is different.

Notice that we have incremented the host port numbers, as the port numbers will get used by the leader container, we will need different port numbers for the follower node. So in my case I have incremented the port numbers by 1.

after executing the above commands you will have two containers one above another, ready for our implementation. 

![Containers after starting up](/assets/images/step-1-docker-containers-started.png)


For the duration of the tutorial, I will be executing commands for leader in the top terminal and the commands for the follower in the bottom terminal.

Lets move to step II


### **Step II - Preparing the machines, installing prerequisites**

JBOSS requires a few softwares to work such as java. also we would require some softwares to work properly on the container such as a text editor, a network management tool etc. 
Let install all these dependencies and required software. 

Also note that, although CentOS uses yum as the package manager, as a personal preference I use `dnf` as the package manager. So lets first install dnf.

ppWe execute the following commands on both the leader and follower containers.

```shell
yum install dnf -y
```

After installing the dnf package manager, lets install other packages using dnf. 

```shell
dnf install java nano emacs sudo java unzip java-1.8.0-openjdk java-1.8.0-openjdk-devel openssh-clients -y
```

Although we can do most stuff being a root user. I prefer not using the root user at all times.
So lets add another user to the containers, make them administrators, set a password for them, and switch to that user. 

**On leader **
```shell
adduser leader
usermod -aG wheel leader
passwd leader
su leader
```

**On follower **

```shell
adduser follower
usermod -aG wheel follower
passwd follower
su follower
```

### **Step III - Download JBOSS**

Now lets download JBOSS setup on both of our containers.

The JBoss EAP ZIP file is available from the Red Hat Customer Portal.

###### Downloading the JBoss EAP ZIP File

- Open a browser and log in to the Red Hat Customer Portal at https://access.redhat.com.
- Click Downloads.
- Click Red Hat JBoss Enterprise Application Platform in the Product Downloads list.
- Select the correct JBoss EAP version from the Version drop-down menu.
- Find Red Hat JBoss Enterprise Application Platform 7.x.x in the list and click the Download link.

You might be required to sign up to the portal or do the `provide us some information shenanigans` before you could get access to the download. But you will reach to it anyways. Once you get the zip transfer them to the container using scp, or else once you get the link, download it directly inside the container using wget.

###### Installing the Downloaded zipfile.

Unzip the JBOSS zip
```shell
unzip jboss-eap-7.2.0.zip
cd jboss-eap-7.2.0
```
after doing this my leader and follower terminals look like this.

![](/assets/images/2019-02-14_18-17.png)


###



### **Step V - Run JBOSS**


### **Step VI - JBOSS Management Interface overview**


