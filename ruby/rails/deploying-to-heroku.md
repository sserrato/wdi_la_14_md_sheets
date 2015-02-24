#Deploying to Heroku

1. Navigate to your app's directory in Terminal. Make sure to have a Git repo set up for the directory.
	
2. Run ```$ heroku create app-name```
	+ You can just use the command
	
		```$ heroku create```
	
		but Heroku will create a name for you, and they're usually weird.
	
3. Verify the remote in your git configuration via 
	
	```$ git remote -v```.

4. To precompile assets (CSS, images), run

	```$ RAILS_ENV=production bundle exec rake assets:precompile```.

5. To deploy run, 

	```$ git push heroku master```.
	


###After the first deployment

After you've created the Heroku app and deployed, continue making changes and writing code. To see the changes reflected on Heroku, you need to push again.

You have to push all changes to Github then deploy to Heroku. That is,

```
	$ git add -A
	$ git commit -m "commit message"
	$ git push origin master
	$ RAILS_ENV=production bundle exec rake assets:precompile
	$ git push heroku master
	
```