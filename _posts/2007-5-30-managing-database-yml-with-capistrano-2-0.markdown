--- 
layout: post
title: Managing database.yml with Capistrano 2.0
---
Jeremy Voorhis posted [a really great Capistrano recipe for managing database.yml](http://www.jvoorhis.com/articles/2006/07/07/managing-database-yml-with-capistrano) which dynamically creates a database.yml file in your shared directory on setup, and symlinks your app's database.yml once it's deployed.  This is great if you don't version control your database.yml file for security reasons or working with multiple developers.  

[Capistrano 2.0](http://www.capify.org/) changes the syntax for task callbacks and gets rid of the useful render method.  However, using [ERb](http://www.ruby-doc.org/stdlib/libdoc/erb/rdoc/), Ruby's built-in templating system, isn't much more difficult than using the old render method.  Here is Jeremy's script updated for Capistrano 2.0 using ERb and the new namespaced callback syntax.

		require 'erb'

		before "deploy:setup", :db
		after "deploy:update_code", "db:symlink"

		namespace :db do
		  desc "Create database yaml in shared path"
		  task :default do
		    db_config = ERB.new <<-EOF
		    base: &base
		      adapter: mysql
		      socket: /tmp/mysql.sock
		      username: #{user}
		      password: #{password}
    
		    development:
		      database: #{application}_dev
		      <<: *base

		    test:
		      database: #{application}_test
		      <<: *base
    
		    production:
		      database: #{application}_prod
		      <<: *base
		    EOF
  
		    run "mkdir -p #{shared_path}/config"
		    put db_config.result, "#{shared_path}/config/database.yml"
		  end

		  desc "Make symlink for database yaml"
		  task :symlink do
		    run "ln -nfs #{shared_path}/config/database.yml #{release_path}/config/database.yml"
		  end
		end

Until I get better syntax highlighting for this blog, check out the [Pastie for the color version](http://pastie.caboo.se/67170).  For more info on whats new in Capistrano 2.0, check out [Jamis' preview](http://weblog.jamisbuck.org/2007/5/11/capistrano-2-0-preview-2) and [Geoff's post](http://nubyonrails.com/articles/2007/04/27/tips-for-upgrading-to-capistrano-2).  Also, props to Jamis for suggesting I use ERb directly.

**Update:** Updated code to use its own :db namespace instead of the default one.  The database yaml file will be created by the default :db task, and the symlink will be created by the db:symlink task.  Note how namespaces in Cap 2.0 allows us to have two symlink tasks, one in the deploy namespace and the other in db.
