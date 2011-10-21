--- 
layout: post
title: Spacer, Yes with an 'e', Released
---
![Image](/images/2008/2/11/2245964951_69fdb18688_o.jpg)

*DESCRIPTION*

Ruby API for the MySpace Platform REST API

*FEATURES/PROBLEMS*

* Implements v1.0 of the MySpace Platform REST API
* Uses OAuth to securely authenticate with MySpace
* Uses JSON for minimal transport footprint

*PLAY*

![Image](/images/2008/2/11/2246938994_11c6d63b2e.jpg)

	@myspace = Spacer::Client.new(api_key, secret_key)
	user = @myspace.user('3454354')
	puts user.interests.music
	puts user.photos.first.caption

*REQUIREMENTS*

* OAuth
* ActiveSupport
* Mocha (for testing)

*INSTALL*

* sudo gem install spacer

*DOCUMENTATION*

Rubyforge: [http://rubyforge.org/projects/spacer/](http://rubyforge.org/projects/spacer/) \(submit bugs here\)

RDocs: [http://spacer.rubyforge.org/](http://spacer.rubyforge.org/)

Goolge Group: [http://groups.google.com/group/spacer-ruby](http://groups.google.com/group/spacer-ruby)

*NOTES*

MySpace is still actively making changes to their API, so this is far from a 1.0 release.  However, as of the day of this post, it implements all the features of their REST API.  

Thanks to Ken Pelletier for coming up with the very creative name.
