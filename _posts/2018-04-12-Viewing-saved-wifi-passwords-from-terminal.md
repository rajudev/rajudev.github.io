---
title: "Viewing-saved-wifi-passwords-from-terminal"
categories:
  - Markdown
tags:
  - shell
  - Wi-Fi
  - wireless
  - CLI
  - terminal
  - bash
  - security
last_modified_at: 2018-06-01T12:25:10-05:00
---

### Overview
Often at times you want to know the passwords of a particular WiFi connection 
that you are connected to or of one that you connected in the past. 

### Where the wifi network details are saved?
The instructions that I am going to write apply to most distributions and the 
ones which use the `network-manager` package for managing the networks.

The Wifi networks you have ever connected to are stored in `/etc/NetworkManager/system-connections`

```sh
root@sanganak:/etc/NetworkManager/system-connections# pwd
/etc/NetworkManager/system-connections
```
This is where all the wifi network details are stored. 
Lets see some saved networks from my computer. 


```sh
root@sanganak:/etc/NetworkManager/system-connections# ls -la
total 36
drwxr-xr-x 2 root root 4096 Aug 23 16:51  .
drwxr-xr-x 7 root root 4096 Aug 15 02:57  ..
-rw------- 1 root root  335 Aug 22 00:45  Aryan
-rw------- 1 root root  338 Aug 18 13:07  GUEST-N
-rw------- 1 root root  345 Aug 23 16:51  TBSWPRO
-rw------- 1 root root  343 Aug 23 10:16  TP-LINK
-rw------- 1 root root  343 Aug 19 22:54  Tenda_3563
-rw------- 1 root root  341 Aug 19 14:25  hotspot2
-rw------- 1 root root  384 Aug 19 22:41 ''$'\340\244\270\340\245\207\340\244\265\340\244\276'
```
When we connect to any wifi network using the GUI of Network Manager or any
command line interface. The network details are stored in this particular path 
with a new file each time corresponding to the SSID of the network. 

You can open any of these files and the network details would be right there. 

Lets take a look at the network details of `GUEST-N`

```sh
root@sanganak:/etc/NetworkManager/system-connections# cat GUEST-N 
[connection]
id=GUEST-N
uuid=ed2a8866-7a0b-4cb1-96f9-0518ae77806d
type=wifi
permissions=

[wifi]
mac-address=A0:88:B4:E4:C5:64
mac-address-blacklist=
mode=infrastructure
ssid=GUEST-N

[wifi-security]
auth-alg=open
key-mgmt=wpa-psk
psk=esya@2018

[ipv4]
dns-search=
method=auto

[ipv6]
addr-gen-mode=stable-privacy
dns-search=
method=auto

```
You can see that the security key is listed in front of the field `psk`

Lets take a look at more details of another network named `Tenda_3563`

```sh
root@sanganak:/etc/NetworkManager/system-connections# cat Tenda_3563 
[connection]
id=Tenda_3563
uuid=6e3fcf66-1a04-4f7b-a931-90881d9ea132
type=wifi
permissions=

[wifi]
mac-address=A0:88:B4:E4:C5:64
mac-address-blacklist=
mode=infrastructure
ssid=Tenda_3563

[wifi-security]
auth-alg=open
key-mgmt=wpa-psk
psk=12345678

[ipv4]
dns-search=
method=auto

[ipv6]
addr-gen-mode=stable-privacy
dns-search=
method=auto
```
For the network `Tenda_3563` the password listed above is `12345678`

So now we know the wifi network connection details and where they are stored.
