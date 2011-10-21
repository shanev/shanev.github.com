--- 
layout: post
title: Using Xcode with Git
---

{{ page.title }}
================

For Xcode and Git to work smoothly with each other, you need to make sure Git treats Xcode project files properly.  You do this by configuring Git via .gitignore and .gitattributes.  Create these files in your repo's root folder and add the following lines:

\.gitignore

	# xcode noise
	build/*
	*.pbxuser
	*.mode1v3

	# old skool
	.svn

	# osx noise
	.DS_Store
	profile

\.gitattributes

	*.pbxproj -crlf -diff -merge

The line in .gitattributes treats your Xcode project file as a binary.  This prevents Git from trying to fix newlines, show it in diffs, and excludes it from merges.  Note that you will still see it shown as a conflict in merges, although the file won't have changed.  Simply commit it and things should be good.

Thanks to [Jonathan Wight](http://twitter.com/schwa/statuses/853833491) and [Chris Double](http://www.bluishcoder.co.nz/2007/09/git-binary-files-and-cherry-picking.html).
