--- 
layout: post
title: Rails Stats Plugin or Show Me Those Pretty Graphs
---
I present to all five of you, my very first Rails plugin.  Rails Stats is a basic graphical version of the Rake 'stats' task.  It generates a graph showing your lines of code versus lines of test code, and two other graphs that may be useful to some of you visually driven folks.  It could also be used by people outside of development, such as managers, to track the progress of your project.

In order for this plugin to work, you must have [Gruff Graphs](http://nubyonrails.com/pages/gruff) installed.  After you have Gruff Graphs running successfully, install the plugin with:

	script/plugin install http://shanesbrain.net/svn/rails/plugins/rails_stats

If your project is under Subversion version control, I highly recommend doing:

	script/plugin install -x http://shanesbrain.net/svn/rails/plugins/rails_stats
		
to automatically use svn:externals which enables easy plugin updates with the 'svn update' command.  Since I'm an iterative development type of guy (lazy and haven't included any tests), this is a good idea.

To run it, simply point your brower to yourapp/rails_stats.
For example, [http://shanesbrain.net/rails_stats](http://shanesbrain.net/rails_stats)
shows Rails Stats running on the current Typo trunk. 

I don't plan on expanding on this plugin too much, although I do want to add a graph showing green/red lines for test status and possibly integration with Subversion to show the last few commits.  

I also finally got a chance to get my Subversion repository online, so you can browse the code at [http://shanesbrain.net/svn/rails/plugins](http://shanesbrain.net/svn/rails/plugins).  There isn't much documentation or tests since this plugin was so simple, but let me know if there is anything I missed.  Feedback is welcome!
