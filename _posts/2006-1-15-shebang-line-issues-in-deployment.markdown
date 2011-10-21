--- 
layout: post
title: Shebang Line Issues in Deployment
---

{{ page.title }}
================

When you start a new Rails project using the rails generator, it creates a shebang line in dispatch.fcgi specific to where ruby is installed.  For example, on FreeBSD, the line is 

	#!/usr/local/bin/ruby18

On Mac OS X, the line is 

	#!/opt/local/bin/ruby

I use FreeBSD in my production environment and OS X in my development environment.  Instead of maintaining two different dispatch.fcgi files or adding extra logic to the files, you can easily solve this problem by making a symlink in the development environment.

I first changed the line to the appropriate one for my production environment, and then created the following symlink.

	sudo ln /usr/local/bin/ruby18 /opt/local/bin/ruby

This is probably more of an issue for people on vastly different platforms.  However, since FreeBSD and OS X are so similar, I might just standardize on /usr/local/bin/ruby.
