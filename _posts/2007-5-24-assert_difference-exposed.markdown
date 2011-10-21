--- 
layout: post
title: assert_difference Exposed
---
assert_difference is my favorite Rails test helper, and until a few weeks ago, was sitting in a helper class that I used to add to all my projects.  It is now in Rails core.  There were a few versions of it floating around, so it is good that we now have only one version to deal with. 

**What can you do with it?**

One of the most common idioms I've run into in testing, is to count the number of records associated with a Model, create a new one, and make sure the count incremented by one.  In the old days, we had to do this:

	def test_should_create_user
	  num_users = User.count
	  user = create_user
	  assert !user.new_record?, "#{user.errors.full_messages.to_sentence}"
	  assert_equal num_users + 1, User.count
	end

Now we can do:

	def test_should_create_user
	  assert_difference 'User.count' do
	    user = create_user
	    assert !user.new_record?, "#{user.errors.full_messages.to_sentence}"
	  end
	end

We saved one line, and got rid of repeating <code>User.count</code>.  assert\_difference gets very close to my limit of too much magic, but I still like how it cleans up tests, especially if you use it with assert\_no\_difference as well.  You aren't forced to use it, just like you aren't forced to scaffold.

**How does it work?**

Here is what the source looks like:

	 # File vendor/rails/activesupport/lib/active_support/core_ext/test/difference.rb
	22:       def assert_difference(expression, difference = 1, &block)
	23:         expression_evaluation = lambda { eval(expression, block.binding) }
	24:         original_value        = expression_evaluation.call
	25:         yield
	26:         assert_equal original_value + difference, expression_evaluation.call
	27:       end

We pass in our expression <code>'User.count'</code>, the default difference of 1, and the block to assert_difference.  We then evaluate the expression <code>User.count</code> and store it in a Proc object, since lambda converts a block to a Proc object.  A Proc object allows us to store a chunk of code and evaluate it at a later time, while maintaining the context of its original definition.  If we currently have 3 users, <code>original\_value</code> will have a value of 3 in line 24.  Then we yield to the block and create the new user.  Finally we will add 1 to the <code>original\_value</code> of 3 and re-evaluate the expression <code>User.count</code> by calling the Proc object.  Since the new user was created, the User count is now 4 and the test will pass.  Notice how eval is passed in the binding of the block.  This causes the evaluated expression to run in the context of the block.  I don't think this makes a difference in this specific example, but it makes sense, since <code>User.count</code> is more associated with the block than the top-level binding of the test method.

**Why are you telling me all this?**

Of course you don't need to know all of this to use assert_difference.  I just thought it was a well written method that demonstrates practical use of Proc objects.

**Update**:

If you are using acts\_as\_authenticated or restful\_authentication, you will have to go in and change your model unit test to use <code>assert\_difference 'Model.count' do</code> instead of <code>assert\_difference Model, :count do</code>.  If you are working on a new project and going to use aaa, use [this patch](http://pastie.caboo.se/64280) to fix your tests.
 
