--- 
layout: post
title: "> YouTube Gem 0.8.6 Released"
---
This is mainly a bugfix release but also makes it easier to search for videos by category.  Searching by category greatly helps in finding videos that are more relevant.  You can now do:

    videos = videos_by_category_and_tag(YouTube::Category::MUSIC, 'bush')

or if you wanted to:

    videos = videos_by_category_and_tag(YouTube::Category::NEWS_POLITICS, 'bush')

For more details check out the [CHANGELOG](http://viewvc.rubyforge.mmmultiworks.com/cgi/viewvc.cgi/trunk/CHANGELOG?root=youtube&view=markup).  Thanks to all the contributers, [Walter Korman](http://lemurware.blogspot.com/), [Lucas Carlson](http://rufy.com/), Rob Tsuk, and Thomas Cox.  

Related posts:<br/>
[More YouTube Library Goodness](http://shanesbrain.net/articles/2007/02/12/more-youtube-library-goodness)<br/>
[YouTube Library 0.8.0 Released](http://shanesbrain.net/articles/2006/11/21/ruby_youtube_library_0_8_0_released)<br/>
[A Ruby Interface to the YouTube API](http://shanesbrain.net/articles/2006/09/28/a-ruby-interface-to-the-youtube-api)
