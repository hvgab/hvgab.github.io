---
layout: post
title: "Connect Atlassian Sourcetree to on-prem git-server"
date:
categories: atlassian sourcetree git
---

# Connect Windows SourceTree to Linux Git Server

You have SourceTree on your local _windows_ computer.  
You have a git repository on an on-prem linux server.  
You want to clone a git-project from your on-prem server.  
You usually connect to the server with ssh.

## Install SourceTree

Download and install sourcetree from their website.

## Generate SSH-key

Do not generate your new ssh-key with putty, in PowersHell just type `ssh-keygen` and press enter all the way.

## Copy the ssh-key to the linux server

Copy the ssh-key to your linux server with
`type $env:USERPROFILE\.ssh\id_rsa.pub | ssh username@hostname_or_ip "cat >> .ssh/authorized_keys"`

`type $env:USERPROFILE\.ssh\id_rsa.pub` prints out the ssh key.  
Pipe that into the `cat` which in turn adds it to the bottom of the `.ssh/authorized_keys` file.

Check that you can ssh into you server with your new key without password.
`ssh username@hostname_or_ip`
and you should enter the server without typing you password.

## Change Sourcetree from Putty/Plink to OpenSSH

In sourcetree go to `tools` -> `options`

Change "SSH Client" from Putty/Plink to OpenSSH.
Add your privatekey (id_rsa) to the "SSH Key" field.
You can also add your key (or more keys) from "Tools->add ssh key"

## Clone your git repository

Clone your git repository from the "clone" menu.
The address should then be "username@hostname_or_ip/projectname.git"
Voila, no errors.

---

#### Search Tags

Git Remote: Error: fatal: protocol error: bad line length character:
