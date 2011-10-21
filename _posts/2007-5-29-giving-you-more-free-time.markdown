--- 
layout: post
title: Giving You More Free Time
---
[Sexy migrations](http://ryandaigle.com/articles/2007/5/6/what-s-new-in-edge-rails-bringin-sexy-back) (and previously [Hobo](http://www.hobocentral.net/) and the [Sexy Migrations plugin](http://errtheblog.com/post/2381)) gave us automatic <code>created\_at</code> and <code>updated\_at</code> fields in our migrations, using the <code>timestamps</code> keyword.  

How about bringing some of this sexiness to generators and taking it a step further? Well my [patch](http://dev.rubyonrails.org/changeset/6883) was accepted and Rails now automatically adds timestamps to all generated migrations.  So when you generate a model, scaffold, or resource, you will get timestamps for free.  It is the equivalent of adding <code>created\_at:datetime</code> and <code>updated\_at:datetime</code> to your generators.  So <typo:code>script/generate model post title:string</typo:code> will do the same thing as <typo:code>script/generate model post title:string created\_at:datetime updated\_at:datetime</typo:code>  

This is nothing significant but I hope it saves people a few keystrokes.  If you don't need timestamps you can always just delete the associated lines from your migration file and the fixtures.  Just another example of Rails making it easier to do common things.  This is currently only available in Edge Rails.


