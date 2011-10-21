--- 
layout: post
title: Acts As Most Popular Rails Plugin
---
Make your models feel like they are in high school again.  This plugin retrieves the most frequently occurring values for each column.  It adds methods of the form most\_popular\_\[pluralized\_column\_name\].  You can control how many results you get with the :limit option.  The default limit is 5.

For example, lets say you have a Person model that has a name, age, and city.

		class Person < ActiveRecord::Base
		  acts_as_most_popular
		end

This will give you the methods:

* most\_popular_names
* most\_popular_ages
* most\_popular_cities

For example, lets say you have six people in your database. Three are from Chicago, two from New York, and one from Hartford.  Then, most\_popular_cities will give you:

		Person.most_popular_cities
		=> ["chicago", "new york", "hartford"]

Each most\_popular method returns an array of the type of the column.  Check out  [this unit test](http://shanesbrain.net/svn/rails/plugins/acts_as_most_popular/test/>) for more examples.

Install with:

		script/plugin install http://shanesbrain.net/svn/rails/plugins/acts_as_most_popular

Feedback appreciated.

**Update**: I can't take credit for the name of this plugin.  Someone on the #rubyonrails channel came up with it.

**Update**: The author of [Ruby Inside](http://www.rubyinside.com/acts_as_most_popular-data-popularity-extension-for-rails-models-177.html) suggests that this could be used as some sort of [Calculation](http://api.rubyonrails.com/classes/ActiveRecord/Calculations/ClassMethods.html).  I think it could easily be made a *mode* Calculation instead of an Acts As plugin, since popularity is basically the mode in decreasing order.  What do you guys think?
