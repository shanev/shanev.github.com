--- 
layout: post
title: More YouTube Library Goodness
---
I just checked in YouTube Library v0.8.5 to the trunk and uploaded the new gem.  It fixes a few bugs that have been bugging you guys for a while, and includes some new methods the guys over at Google/YouTube were kind enough to add.  Namely:

		- youtube.videos.list\_by\_related (with paging),
		- youtube.videos.list\_by\_playlist (with paging),
		- youtube.videos.list\_by\_category (with paging)
		- youtube.videos.list\_by\_category\_and\_tag (with paging)

The category and tag search will greatly help in filtering out unwanted videos compared to regular tag searches.  Tests for these methods have been included too.  Just update or install the <code>youtube</code> gem.

I also created a Google Group to discuss issues and bugs.  If you are a casual user, developer, or just interested in the progress of this library, please sign up below.  All future announcements regarding this library will be posted to the group.

		<table border=0 style="background-color: #fff; padding: 5px;" cellspacing=0>
		  <tr><td>
		    <img src="http://groups.google.com/groups/img/3/groups_bar.gif"
		         height=26 width=132 alt="Google Groups Beta">
		  </td></tr>
		  <tr><td style="padding-left: 5px">
		    <b>Subscribe to Ruby YouTube Library</b>
		  </td></tr>
		  <form action="http://groups.google.com/group/ruby-youtube-library/boxsubscribe">
		  <input type=hidden name="hl" value="en">
		  <tr><td style="padding-left: 5px;">
		    Email: <input type=text name=email>
		           <input type=submit name="sub" value="Subscribe">
		  </td></tr>
		</form>
		<tr><td align=right>
		  <a href="http://groups.google.com/group/ruby-youtube-library?hl=en">Visit this group</a>
		</td></tr>
		</table>


YouTube seems to be having some issues with category and category/tag search at the moment, so I commented out those tests.  As soon as they fix it, I will uncomment the tests and they _should_ pass.  Follow this [thread](http://groups.google.com/group/youtube-api-issues/browse_thread/thread/28ea02c81f23b56e) over at the YouTube Developer's group to learn more.

Related posts: 

- [\[ANN\] YouTube Library 0.8.0 Released](http://shanesbrain.net/articles/2006/11/21/ruby_youtube_library_0_8_0_released)
- [A Ruby Interface to the YouTube API](http://shanesbrain.net/articles/2006/09/28/a-ruby-interface-to-the-youtube-api)
