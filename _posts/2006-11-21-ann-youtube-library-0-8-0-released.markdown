--- 
layout: post
title: "[ANN] YouTube Library 0.8.0 Released"
---

{{ page.title }}
================

**Documentation**: [http://youtube.shanesbrain.net/](http://youtube.shanesbrain.net/)

**RubyForge project page**: [http://rubyforge.org/projects/youtube/](http://rubyforge.org/projects/youtube/)

My little YouTube Library has finally reached version 0.8.0, thanks to a sizable patch by [Walter Korman](http://lemurware.blogspot.com/), and some functional programming tips by [Lucas Carlson](http://tech.rufy.com/).  It now includes full unit tests, which can be run using <code>rake</code>, and all classes are under the YouTube namespace.  Please note that this version breaks backwards compatibility.  If you want to upgrade or install, do <code>gem install youtube</code>.  You can still get the old version with <code>gem install youtube --version 0.1.1</code>.

**Namespace**

All classes are under the YouTube namespace.  To create a new YouTube client, you now have to do: <typo:code>youtube = YouTube::Client.new 'DEVELOPER ID'</typo:code>

**Object Mapping**

Results from YouTube are converted to corresponding Ruby objects.  For example, <code>video.view\_count</code> will return an Integer, and <code>video.rating\_avg</code> will return a Float.

**Embed HTML**

Everyone wants to use this to embed videos on their Web3.1 site, no? Walter added the method <code>embed\_html</code> which takes in a width and height (or uses the default values) and outputs all the HTML you need to embed the Flash video on your site.  Therefore, in a Rails view, you can do something like: <typo:code><%= video.embed\_html %></typo:code>

**Unit Tests**

Run unit tests with <code>% rake test</code>.  This allows for easy detection if YouTube ever changes their API on us.

**Video Details**

I got a lot of questions after the first release about how to get video details, so here in an example:

	video = featured_videos.first       # returns a YouTube::Video object
	details = video_details(video.id)   # returns a YouTube::VideoDetails object
	@tags = details.tags                # returns a String for all tags for this video


In a similar vein to this library, Walter has released a [Google Video API for Ruby](http://lemurware.blogspot.com/2006/11/google-video-api-for-ruby.html) that brilliantly uses Hpricot to parse video meta-data.
