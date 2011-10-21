--- 
layout: post
title: Prototyping and Test Driven Development
---
Test-driven development is probably the hardest of the Agile methods to get used to doing.  Since Rails makes web development so easy, it is not hard to be tempted into rushing into code.  But you know you feel guilty for doing it.  Especially since Rails generates all those test harness files that you never touch.  You know you have trouble sleeping at night because of those empty files.  Is there a shortcut? The short answer: No.  Write your tests.  But there is a way to alleviate this burden.  I think of code I write that don't have tests as prototype code.  If you want to develop that killer Web 2.0 app in no time without worrying about tests, you can do it, as long as you think of the test-free version as a prototype.  Then you can always go back and re-write the entire thing from scratch with tests.  I believe with the productivity gains of Rails, this is totally possible.

In terms of iterative development, the prototype can be iteration _n-1_.  Then iteration _n_ would be a complete test-driven re-write.  You will learn from your mistakes in iteration _n-1_ and end up with much cleaner code.  Once you get used to writing tests, you will find that you are actually more productive when you write tests than when you don't.  You tend to spend less time trying to figure out one-liner bugs since good tests will help flush these out before they are a problem.

You don't always have to get it right the first time.  Artists and sculptors often go through many iterations of their work before finishing the final product.  Why would software development be any different?

Have a real world job where you have to come up with an estimate and project plan? Instead of coming up with a haphazard estimate, include  the prototype in the estimation phase.  In many cases, your client or boss wouldn't mind giving you a little extra time to come up with a more accurate estimate.  You will end up with a better idea about the pitfalls of your project.  

