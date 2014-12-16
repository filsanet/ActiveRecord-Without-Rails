ActiveRecord Without Rails, JDBC-Mssql style
============================================

This is a mashup of:

* https://github.com/jwo/ActiveRecord-Without-Rails
* http://exposinggotchas.blogspot.jp/2011/02/activerecord-migrations-without-rails.html  

The Gemfile can be configured for a combo of JRuby, JDBC, and Microsoft MSSQL server, as well as for a combo of MRI Ruby (tested on 2.1.2) and SQLite3/Postgres.

---


What you can do
---------------

Just a simple example of using ActiveRecord migrations without Rails

### run rake tasks:

* `rake db:create`
* `rake db:migrate`
* `rake db:drop`
* `rake db:rollback`
* `rake db:version`


### Or, you can run the thing to show that it'll connect

```
ruby ar-no-rails
```

Output:
> Count of Pages: 0

### Lastly, you can IRB it to do stuff:

$ irb

```
>> require "./ar-no-rails"
=> true
>> Page.new
=> #<Page id: nil, content: nil, published: false>
>> Page.create content: "the-content"
=> #<Page id: 1, content: "the-content", published: false>
```

Pre-requisites
--------------

For the JRuby/JDBC option, you'll need:

* Java (tested on Java 6)
* JRuby
* A Mssql database server

Note: This project is configured for  Rails 3.2.13, because I have to use Java 6 in my current environment. 
Rails 4.0 would force an upgrade of the JDBC drivers, which require Java 7. 


Usage
-----

### Getting Started

1. Download the zip file (or git clone)
2. Unzip the archive.
3. rename folder to your project name: `mv ActiveRecord-Without-Rails-JDBC-Mssql myproj`
4. `cd myproj`
5. `bundle install`
6. configure the database in config/database.yml
7. `rake db:version` # check to see that the db config is correct.
8. `rake --tasks` make sure everything is working okay

### config/database.yml

The database.yml is set up to allow for different environments.
By default it has one environment, `development` defined.

If you define a `production` environment in the config/database.yml, you can use `DATABASE_ENV=production rake db:version` to run against the production environment.
(this is different from the RAILS_ENV you will see in a lot of Active Record migration documentation because... well, we are not using rails here.)


Alternatives
------------

I haven't checked this out yet, but there is a standalone-migrations gem:

* http://gabrito.com/post/standalone-migrations-using-rails-migrations-in-non-rails-projects
* https://github.com/thuss/standalone-migrations

