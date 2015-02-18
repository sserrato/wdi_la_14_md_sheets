# SQLite to PostgreSQL

Ruby on Rails and some other web based frameworks ship with support for a small database called sqlite3 by default. SQLite is ideal for users getting started since it can be run in memory and backed by small files on disk that are easily created and moved around. While easy to use, SQLite is not intended as a production grade database. Instead Heroku provides production grade PostgreSQL databases as a service.

This is taken from the Heroku site [here](https://devcenter.heroku.com/articles/sqlite3)

The easy way to use Postgres is to implement it at the start of a new Rails app. Use: 

` $ rails new -d postgresql`

This will install the `pg` gem in your `Gemfile` and write the correct `config/database.yml` configuration locally.

## To convert from an existing Rails app

Open the `gemfile` and remove the sqlite3 gem by commenting out this line:

``gem 'sqlite3'``

Replace it with this line:

``gem 'pg'``

Then run ``bundle install`` or just ``bundle``.

Next you will need to convert your ``config/database.yml``. Open the existing file, which might look something like this:

	development:
	  adapter: sqlite3
	  database: db/development.sqlite3
	  pool: 5
	  timeout: 5000

	test:
	  adapter: sqlite3
	  database: db/test.sqlite3
	  pool: 5
	  timeout: 5000

	production:
	  adapter: sqlite3
	  database: db/production.sqlite3
	  pool: 5
	  timeout: 5000
	  

You will need to change the adapter from this: 

``  adapter: sqlite3``

To this: 

``adapter: postgresql``

Note the adapter name is `postgresql` not `postgres` or `pg`. You will also need to change the `database:` to a custom name. A final version might look something like this:


	development:
	  adapter: postgresql
	  database: my_database_development
	  pool: 5
	  timeout: 5000
	test:
	  adapter: postgresql
	  database: my_database_test
	  pool: 5
	  timeout: 5000

	production:
	  adapter: postgresql
	  database: my_database_production
	  pool: 5
	  timeout: 5000
	  
	  
Once you’ve installed the `pg` gem and migrated your `config/database.yml` file you will need to create your database and run any pre existing migrations against it:

	$ rake db:create
	$ rake db:migrate
	
Now you should be good to go. Now when you push to Heroku using Rails a [development grade postgres](https://devcenter.heroku.com/articles/heroku-postgres-plans#hobby-tier) instance will be provisioned and connected to your app automatically. If you’re not using Rails, you may need to manually add the postgres addon by running`

#Getting a SQLite error even though it is not in the Gemfile

If you’ve removed the gem `'sqlite3'` line from your `Gemfile` and are still getting errors while deploying to Heroku it is likely that another gem you are using has `sqlite3` as a dependency. To help find the source of this dependency look in your `Gemfile.lock` for sqlite3. Find the gem that has sqlite3 as a dependency and remove it from your `Gemfile`. Once you’ve done this run `bundle install` and ensure that `sqlite3` no longer exists in your `Gemfile.lock`.