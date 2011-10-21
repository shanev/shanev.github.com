--- 
layout: post
title: FeedBurner Auto-Discovery Links in Typo
---
Damien Tanner has a [nice article](http://iamrice.org/articles/2006/03/30/migrating-typo-feeds-to-feedburner) on how to migrate Typo feeds to FeedBurner.  However, to make it more complete, I added the following steps:

Too many options are a bad thing.  When you give your readers a multiple range of choices such as RSS, RSS 2.0, Atom, etc., you will get chunks of readers using each format, making it hard to track subscriptions.  Damien suggests redirecting these URLs to your FeedBurner URL.  If you have FeedBurner's SmartFeed option enabled, then any RSS reader supporting any format should be able to parse your feed.  However, it would be better to take it one step further and only allow your readers one feed option.  To do this in Typo, edit the file app/helpers/articles_helper.rb and change your auto-discovery URLs (around line 60):

		feedburner_url = "http://feeds.feedburner.com/YOUR_FEED"
		. . . 
		<link rel="alternate" type="application/atom+xml" title="Atom" href="#{ feedburner_url }" />
		<link rel="alternate" type="application/rss+xml" title="RSS" href="#{ feedburner_url }" />

Then go to the Admin console and empty your cache.  Hit your main blog page to make sure it worked:

		$ curl http://yourblog.tld | grep "link rel"

You should see something like this:

		<link rel="alternate" type="application/atom+xml" title="Atom" href="http://feeds.feedburner.com/ShanesBrainExtension" />
		<link rel="alternate" type="application/rss+xml" title="RSS" href="http://feeds.feedburner.com/ShanesBrainExtension" />

Be DRY and combine your redirects into one line.  For Apache:

		RedirectMatch permanent ^/xml/(rss|rss20|atom)/feed.xml http://feeds.feedburner.com/YOUR_FEED

[Josh Knowles](http://joshknowles.com/) suggests this line for Lighttpd in a comment on a [post](http://www.robbyonrails.com/articles/2006/08/22/feedburner-and-lighttpd-redirects) by Robby Russell:

		url.redirect = (â€/xml/(atom|rss|rss20)/feed.xmlâ€ => â€œhttp://feeds.feedburner.com/YOUR_FEEDâ€)

For Apache, you need to have <code>mod\_alias</code> loaded, and <code>mod\_redirect</code> for Lighttpd.

Someone should submit a patch to Typo that enables FeedBurner integration.  An option can be added to the Admin site to get the FeedBurner URL.  Then all the auto-discovery links can be made to point to it.  I'd do it if I had more time.
