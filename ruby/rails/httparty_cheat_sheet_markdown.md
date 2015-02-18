#HTTParty Cheat Sheet

##Index
* Objectives 
* Resources
* API, Getting Started W/Rotten Tomatoes Example 

##Objectives 
* Connect your rails app to an API to get useful data back
* Work with an API response and pick out information to use in your app 

##Resources 
* https://github.com/ga-students/WDI_LA_14/blob/master/06-week/httparty_time.md
* https://github.com/jnunemaker/httparty

##API, Getting Started W/Rotten Tomatoes Example 
1. Find their API doc: http://developer.rottentomatoes.com/
2. Register for Rotten Tomatoes API
3. Make note of your API key
4. Go to the IO docs: http://developer.rottentomatoes.com/iodocs
5. Manipulate data in Postman if you wish, turning on URL Params buttons
6. $ rails new appname 
7. Add gem 'httparty' to Gemfile 
8. $ bundle 
9. $ rails c
10. response = HTTParty.get"URLHERE"
11. Add the following to your controller def index method:
	@response = HTTParty.get"URLHERE"
12. In view, add <%= @response.index %> or <%= @response %> or <%= @response['movies'][0]['title']%>  