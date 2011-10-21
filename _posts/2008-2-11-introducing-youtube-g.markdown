--- 
layout: post
title: Introducing YouTube-G
---
[Walter Korman](http://lemurware.blogspot.com/) and I are proud to release youtube-g version 0.4.1.  

youtube-g is a pure Ruby client for the YouTube GData API. It provides an easy
way to access the latest YouTube video search results from your own programs.
In comparison with the earlier Youtube search interfaces, this new API and
library offers much-improved flexibility around executing complex search
queries to obtain well-targeted video search results.

More detail on the underlying source Google-provided API is available at:

[http://code.google.com/apis/youtube/overview.html](http://code.google.com/apis/youtube/overview.html)

*FEATURES*
  
Aims to be in parity with Google's YouTube GData API.  Core functionality is currently present -- work is in progress to fill in the rest.

*USE*

Create a client:
  
	require 'youtube_g'
	client = YouTubeG::Client.new
  
Basic queries:

	client.videos_by(:query => "penguin")
	client.videos_by(:tags => ['tiger', 'leopard'])
	client.videos_by(:categories => [:news, :sports])
	client.videos_by(:categories => [:news, :sports], :tags => ['soccer', 'football'])
	client.videos_by(:user => 'liz')
        
Standard feeds:
        
	client.videos_by(:most_viewed)
	client.videos_by(:top_rated, :time => :today)
        
Advanced queries (with boolean operators OR (either), AND (include), NOT (exclude)):
        
	client.videos_by(:categories => { :either => [:news, :sports], :exclude => [:comedy] }, :tags => { :include => ['football'], :exclude => ['soccer'] })

*DOCUMENTATION*

Rubyforge project: [http://rubyforge.org/projects/youtube-g/](http://rubyforge.org/projects/youtube-g/)

RDoc: [http://youtube-g.rubyforge.org/](http://youtube-g.rubyforge.org/)

Google Group: [http://groups.google.com/group/ruby-youtube-library?hl=en](http://groups.google.com/group/ruby-youtube-library?hl=en)

*INSTALL*

* sudo gem install youtube-g

Changes:

0.4.1 / 2008-02-11

* Added 3GPP video format \[shane\]
* Fixed tests \[shane\]

0.4.0 / 2007-12-18

* Fixed API projection in search URL \[Pete Higgins\]
* Fixed embeddable video searching \[Pete Higgins\]
* Fixed video embeddable detection \[Pete Higgins\]
* Fixed unique id hyphen detection \[Pete Higgins, Chris Taggart\]

0.3.0 / 2007-09-17

* Initial public release

*NOTES*

_Our previous library, youtube, has been deprecated.  Please use youtube-g from now on._

Who can guess what the name youtube-g is in reference to? Hint: Like us, you probably used [BBS's](http://en.wikipedia.org/wiki/Bulletin_board_system) before the days of the web, when wide adoption of TCP/IP was still a few years away.
