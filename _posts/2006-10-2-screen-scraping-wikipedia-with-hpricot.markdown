--- 
layout: post
title: Screen Scraping Wikipedia with Hpricot
---
Wikipedia is one of the few sites that should have an API but doesn't.  It's a shame, considering it is one of the best sources for free quality content.  Due to this limitation, we have to resort to the pre-historic art of screen scraping.  why's [Hpricot](http://code.whytheluckystiff.net/hpricot/) is my favorite tool to do this.  It uses a _fast_ HTML scanner written in C using [Ragel](http://www.cs.queensu.ca/~thurston/ragel/), the same technology that makes Mongrel so fast.  It allows you to parse HTML using either CSS selectors or XPath, in a similar vein to [jQuery](http://jquery.com/).

The few Wikipedia clients out there only output data in Wikitext format or clear text.  I wanted something that will reproduce the content with basic styling intact, so it can be republished in a similar fashion to Answers.com.  Here is the code to do this:

	require 'hpricot'
	require 'open-uri'

	items_to_remove = [
	  "#contentSub",        #redirection notice
	  "div.messagebox",     #cleanup data
	  "#siteNotice",        #site notice
	  "#siteSub",           #"From Wikipedia..."
	  "table.infobox",      #sidebar box
	  "#jump-to-nav",       #jump-to-nav
	  "div.editsection",    #edit blocks
	  "table.toc",          #table of contents 
	  "#catlinks"           #category links
	  ]

	doc = Hpricot open('wikipedia url')
	@article = (doc/"#content").each do |content|
	  #change /wiki/ links to point to full wikipedia path
	  (content/:a).each do |link|
	    unless link.attributes['href'].nil?
	      if (link.attributes['href'][0..5] == "/wiki/")
	        link.attributes['href'].sub!('/wiki/', 'http://en.wikipedia.org/wiki/')
	      end
	    end
	  end  

	  #remove unnecessary content and edit links
	  items_to_remove.each { |x| (content/x).remove }

	  #replace links to create new entries with plain text
	  (content/"a.new").each do |link|
	    link.parent.insert_before Hpricot.make(link.attributes['title']), link
	  end.remove
	end 

	puts @article.inner_html

For comparison, [here](http://shanesbrain.net/pages/wikipedia.html) is a Wikiepdia article scraped using this script, and its [cousin at Answers.com](http://www.answers.com/screen%20scraping).  Here is the original [Wikipedia article](http://en.wikipedia.org/wiki/Screen_scraping).  There are still a few things to be worked out, like filtering out Javascript and working with other languages.  But I will leave that as an exercise for the reader!

If you are going to use this script, please don't forget to give credit to Wikipedia and include a link to the original article.  It looks like it already does add a Notes section with a link-back which isn't on the original site.  It must be checking the user agent of the browser and adding the line if it detects an unknown browser.  You still have to include a link to the GNU Free Documentation License.

**Update:** \_\_why\_ makes some [suggestions](http://redhanded.hobix.com/inspect/rippingUpWikipediaSubjugatingIt.html) to improve this script, and adds a new method <code>swap</code> which eliminates the ugly <code>end\.remove</code> syntax.
