--- 
layout: post
title: My Top Commands
---


{{ page.title }}
================

	shane$ history | awk '{print $2}' | awk 'BEGIN {FS="|"} {print $1}' |  sort | uniq -c | sort -nr | head -10
	 125 ll
	  99 rake
	  99 cd
	  62 svn
	  21 gem
	  17 rm
	  10 sudo
	   7 curl
	   6 ssh
	   6 mkdir

I use <code>ll</code> (an alias for <code>ls -al</code>) way too much.  What's your command?

--via [OpenSoul](http://opensoul.org/2006/9/27/what-s-your-command).
