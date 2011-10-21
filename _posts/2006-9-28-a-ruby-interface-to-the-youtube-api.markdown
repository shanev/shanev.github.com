--- 
layout: post
title: A Ruby Interface to the YouTube API
---

{{ page.title }}
================

**Update**: [Version 0.8.0](http://shanesbrain.net/articles/2006/11/21/ruby_youtube_library_0_8_0_released) has been released.

We have mashups using maps, links, events, photos, Amazon items, and eBay auctions.  What is the next logic step? Video ofcourse! Learn from the Myspace kids.  They are the future after all.

I present to all of you, my dead simple Ruby interface to the [YouTube REST API](http://youtube.com/dev).  Install with:

	gem install youtube

Want to get the URLs for the top [featured](http://youtube.com/browse?s=rf) YouTube videos?

	require 'youtube'

	youtube = YouTube::Client.new 'developer id'
	videos = youtube.featured_videos
	videos.each { |video| print video.url }

How about the titles of videos with tags ['heel toe technique'](http://youtube.com/results?search_query=heel+toe+technique&search=Search)?

	videos = youtube.videos_by_tag('heel toe technique')
	videos.each { |video| print video.title }

Please check out the [source](http://rubyforge.org/cgi-bin/viewvc.cgi/trunk/?root=youtube) at RubyForge for all available methods.  Also check out the original [YouTube API functions](http://youtube.com/dev).  The interface implements all the YouTube functions currently available.  You will need a YouTube [Developer ID](http://youtube.com/my_profile_dev).

This is a very early version and not used on any production sites yet.  If you run into any issues please let me know.  The YouTube API itself has a couple of inconsistencies that I accounted for, but there may be things I missed.  

I suppose many of you will use this to find videos to embed on your site.  The video URLs returned from the REST interface are made to point to viewable videos on YouTube, and don't work with the <code>embed</code> tag.  Therefore, I created a method on Video called <code>embed_url</code> which will return the URL in the right form.  So make sure you use that one when embedding.

I will put up a page soon with the Rdoc documentation, but the source should be pretty self-explanatory.  Thanks to [flickr.rb](http://redgreenblu.com/flickr/) by Scott Raymond for the inspiration.

This could be used for more than just mashups ofcourse.  The most obvious use is to easily integrate YouTube with your Rails app.

Subversion repository: <code>svn://rubyforge.org/var/svn/youtube</code>
