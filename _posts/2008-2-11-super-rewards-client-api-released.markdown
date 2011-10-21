--- 
layout: post
title: Super Rewards Client API Released
---
*DESCRIPTION*
  
A Ruby client for the $uper Rewards API by KITN Media, the Facebook monetization tool.

*FEATURES*
  
* Aims to implement all the functionality of the $uper Rewards service

*USE*
<code><pre>
offer_code = SuperRewards::Client.offers_display(:iframe, uid)
points = SuperRewards::Client.get_points(uids).first.user.points
</pre></code>

*REQUIREMENTS*

* API / Secret keys for the $uper Rewards service
* Shoulda gem (for testing)

*INSTALL*

* sudo gem install superrewards

*DOCUMENTATION*

Rubyforge: "http://rubyforge.org/projects/superrewards/":http://rubyforge.org/projects/superrewards/

RDocs: "http://superrewards.rubyforge.org/":http://superrewards.rubyforge.org/

*NOTES*

I released this on December 17th, 2007, so the service may have changed since then.  All the tests still pass as of the day of this post.  

Thanks to Eugene from KITN Media for helping me with debugging and testing, and Jason Bailey for moral support.

