Rails Less Migration
=====================

Today I was wanted to use rails goodness inside of my php project. So, I searched online found a solution somewhere.
Fixed it up for any project to use using composer.

I assume you are using tools listed below and know how to use command line.

   * POSIX OS
   * Ruby the programming Language
   * Rake the build tool written in Ruby
   * Activerecord gem, defaults with Rails !!!!


To enable it, add this dependency to your `composer.json` file:

    "rajibahmed/rake-db-migrator": "dev"

Step 1: To enable it in your application you need to create few directories from you terminal :)

    $ mkdir -p db/migrate
    $ mkdir config

Note 1: You do not need to create the structure if you already have it.
Note 2: I have provided a demo database.yml configuration file copy over to config folder.
Important: If you don't have valid database.yml this generator will not work.

Step 2: symlink my rake file to root of you project.

    $ ln -s vendor/rajibahmed/rake-db-migrator/Rakefile .

Step 3: You are done !!


Usage
======

So now you can use this rake file to create and migrate you configured database. Available Rake tasks are,


     rake db:create    # Create the database from config/database.yml for the current DATABASE_ENV
     rake db:drop      # Drops the database for the current DATABASE_ENV
     rake db:generate  # Generate migration files
     rake db:migrate   # Migrate the database (options: VERSION=x, VERBOSE=false).
     rake db:rollback  # Rolls the schema back to the previous version (specify steps w/ STEP=n).
     rake db:version   # Retrieves the current schema version number


Now, Running

    rake db:generate

Will create a template file that you can use as a reference point for writing your first migration.

Note[IMPORTANT] : Class name in a migration file must match the file naming convention. ie.

Name migration file
===================
Now you can pass in the migration file name. But follow the convention underscore word.

    rake db:generate[create_users]

This will generate code like this.


```ruby

     # db/migrate/....._create_user.rb
     CreateUser < ActiveRecord::Migration
     # file name should be timestramp_create_user.rb
     end
```


You are good to go !!! This is a few hours effort. If you want to extend it please fork it or send me emails.

LICENSE: Do whatever you want with it. I don't want money from you and can't be held responsible any fu*k ups. Good luck !!! Simple isn't it.


