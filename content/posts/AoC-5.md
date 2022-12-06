---
title: "AoC#5"
date: 2022-12-06
draft: false
toc: false
images:
tags: ["AoC 2022", "Brute Force", "Passwords", "Hydra"]
---

## [Day 5] 
`Brute-Forcing` He knows when you're awake!

*On the fifth day of christmas:  I find the password that the attackers used to create a backdoor with.*

Task 5: Find the backdoor that the attackers might be using to access Santa's website.

### Remote Access Services.
Remote access to computers and servers has been very useful in connecting to computers/servers that might be in a separate room, building, or country.
Some of this developed software packages and protocols include:
* SSH - secure shell.
* RDP - Remote Desktop Protocol.
* VNC - Virtual Network Computing.

The software or protocol to use is based on the host of the remote computer. If it's a `Linux` host, most 'prolly you'll use ssh.
If it's a `Windows` machine, then RDP will be used. VNC could be used for either. 

### Authentication.
When connecting to the remote computers, an authentication mechanism ought to be in place. Authentication is the backbone of
identity validation. This is important to ensure confidentiality, integrity and avalability of the data/info in the remote computers is maintained.

#### Attacking Passwords.
Back to remote access services, we usually use passwords or private key files for authentication. Using a password is the default method for authentication and requires the least amount of steps to set up. Unfortunately, passwords are prone to a myriad of attacks.

##### The Hydra way...
THC Hydra automates brute-forcing of passwords using a list with common passwords (rockyou.txt or others). Hydra supports many protocols including `ssh`, `vnc`, `ftp` and more.

You can learn more about THC Hydra by joining the [Hydra](https://tryhackme.com/room/hydra) tryhackme room.

###### End of AoC#5