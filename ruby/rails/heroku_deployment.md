#Heroku Deployment

[Rails 4 Heroku Deployment](https://devcenter.heroku.com/articles/rails-4-asset-pipeline) 

[Deploy with Git](https://devcenter.heroku.com/articles/git)

[Heroku Deployment for Rails/PG](https://github.com/mplaza/bunnytest)

[Precompile Not Working!](http://stackoverflow.com/questions/14697604/rails-assets-precompile-just-not-working)



###Checklist (Before you even think of deploying!)

- Does your app work locally? (If you have errors, they won't magically be solved by deploying to Heroku!)
- Do you have seed data/is your app equipped to add objects to your DB? (Locally-stored data won't push up.)
- Are you working from the command line in the app directory?

##Get yourself set up with Heroku

1. If you don't already have one, head on over to Heroku's site and create your own Heroku account
2. After that, go ahead and download the Heroku Toolbelt so you can access Heroku commands in your command shell.
3. in terminal $ heroku login

##Set up a repo for your app

1. Go onto GitHub and create a new repository
2. $ git init in your app directory
3. $ git add -A and git commit -m "some message" so there's something to push
4. $ git remote add origin <yourURLhere>
5. $ git push -u origin master to finish it all off

##Create your Heroku app

2. $ heroku create yourAppName 
3. $ heroku git:remote -a yourAppName
4. add and commit your repo if you haven't already, then... 
5. $ git push heroku master
#####to double check that things worked...
7. $ heroku apps (should see all your heroku apps)
8. $ heroku domains (should see your domain)


##Add the rails_12factor gem

Add the following to your Gemfile: 

1. gem 'rails_12factor'
2. $ bundle install


##Prep your app for precompile
#####Open config/environments/production.rb

2. config.assets.compress = true (compress js and css)
3. config.assets.compile = true (fallback to assets pipeline if a precompiled asset is missed)
4. config.assets.digest = true (generate digests for assets URLs)


## Precompile locally
####In your terminal, run
 
1. $ RAILS_ENV=production bundle exec rake assets:precompile
### Add - Commit - Push

1. git add -A
2. git commit -m "precompiled assets locally"
3. git push origin master
4. git push heroku master
### Rake your seed file (if you have one)
In your terminal, run 
6. $ heroku run rake db:seed (note: this must be done after you've pushed to Heroku, otherwise the seed file won't be recognized)

###After you rake your seed file - Add - Commit - Push
And one last time (following that seed file rake!)

1. git add -A
2. git commit -m "precompiled assets locally"
3. git push heroku master

#You should be up and running!

###if you're running into trouble
1. $ heroku logs (check for errors)
2. Check links at the top of the page.(Rails version?) 
3. **DON'T GIVE UP**