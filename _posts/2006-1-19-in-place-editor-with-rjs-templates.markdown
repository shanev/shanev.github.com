--- 
layout: post
title: In-Place Editor with RJS Templates
---
I ran into a situation while working on a side project, where I needed to update a few elements on the page after performing an in-place edit.  This can happen in a situation where what you are editing is also displayed elsewhere on the page.  You don't want to confuse the user by having the old value as well as the new value on the same page.  This can be accomplished with RJS templates and some slight modifications to the Rails in-place editor macro.  

**NOTE**: RJS templates are like RHTML templates, but for Javascript.  <strike>As of this post, this feature is only available in the current Rails trunk and is not part of the 1.0 release.  You need to be on [EdgeRails](http://wiki.rubyonrails.com/rails/pages/EdgeRails) to use them.</strike>

First, define a method in the controller that will replace the Rails in\_place\_edit\_for macro.  To in-place edit the 'name' attribute of a model named 'Event,' do:

	def set_event_name
	  @event = Event.find(params[:id])
	  previous_name = @event.name
	  @event.name = params[:value]
	  @event.name = previous_name unless @event.save

	  # include logic needed for partials in RJS template
	end

Then create a new file in the view folder called set\_event\_name.rjs.  This needs to include the partial containing the in-place editor view code, as well as anything else you need to update on the page.

	page.replace_html 'in_place_edit_results', :partial => "desc"
	page.replace_html 'upcoming', :partial => "upcoming"
	page.visual_effect :highlight, 'upcoming', :duration => 1
	page.replace_html 'month', :partial => "month"

The view, \_desc.rhtml, can use the built-in Rails macro helper:

	<%= in_place_editor_field :event, :name %>

Check out [this great article](http://shnoo.gr/articles/2005/12/20/ajax-the-great) if you need to validate and sanitize the data.
