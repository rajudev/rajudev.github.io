---
title: "Creating a Debian KVM machine using virt-manager"
categories:
  - Markdown
tags:
  - linux
  - Debian
  - KVM
  - Virtualisation
last_modified_at: 2017-10-24T12:25:10-05:00
---

To-do: Create a Debian 9 KVM machine on a server

Install `virt-manager` to your system

STEP *I* Connect to the host machine which will host KVM machines using its IP adrress in virt-manager

Start `virt-manager`
File --> Add connection
select `Connect to remote host`
Method: SSH
username: username of the remote server
hostname: ip of the remote server

Now the remote machine could be seen as connected in your virt-manager

STEP II Creating the Debian KVM machine

- Click on the button for `Create a new virtual machine`

You can give path of a local install media. I prefer using the `Network Install` option
- Select the `Network Install(HTTP, FTP, or NFS)` option
  Forward
- Give the URL for debian network install repositories.
    Do not give the link for a net install iso images.
    They didn't worked for me.
    The URL should contain the `installer tree` the files required for a system to boot and begin installation like initrd and related files.

  Some of the URLS which will work
    ```
    http://ftp.us.debian.org/debian/dists/stable/main/installer-amd64/
    ```
    or
    ```
    http://cdn-fastly.deb.debian.org/debian/dists/stretch/main/installer-amd64/
    ```

- On the further screens customise the server configurations for CPU or or RAM as required for your setup.
- When you click begin installation wait for your host to pull in the installation files from the remote operating system URL.

- Complete the installation as required.


Further Notes:

To create the machine using command line by using `virt-install` command

To create a debian stretch machine using command line.
```
virt-install --virt-type kvm --name devel-repo-server --location http://cdn-fastly.deb.debian.org/debian/dists/stretch/main/installer-amd64/ --extra-args "console=ttyS0" -v --os-variant debianstretch --disk size=50 --memory 2048
```
you can sheck description of the individual flags by looking at the man page of virt-install `man virt-install`

And you should have a debian KVM machine setup.

Note; This blog post is typed in a hurry & written to be used as a reference for my self and others if I need to revisit the instructions for it.
