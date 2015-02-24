# Rails Commands
Rails Terminal Commands 
$ rails new filename → creates a new rails app file structure in your current directory.
$ rails g → rails generate- that can be used to generate new  models and controllers, all models built this way are singular. 
$ rails s  →  must be run while in your app folder, initializes a local server for your rails app. Ctrl C to kill local server. 
$ rake db:migrate → populates your local database (db) with the data you have built in your rails file structure.  
$ rake db:seed  → populates your database with place holder data for testing purposes
$ bundle install → allows you to install the latest ruby gems. 
$ rails d → deletes and/or rolls back the file structure created by rails g 
$ rails c →  opens rails console 
$ rake routes → returns all open routes for communication between your app and the local server
$ rails db →  opens the database currently linked to your rails root folder 
$ rails db:reset → resets the database 
$ rails g migration RemoveFromModelname  :your_property → removes designated property from schema and migrate files. Must rake db:migrate to see changes. 
$ rails g migration AddFromModelname  :your_property → adds designated property from schema and migrate files. Must rake db:migrate to see changes. 

Rails Console Commands 
$ModelName.all.map(&:your_property) → Returns all objects in the designated model but only displays the values present in the given property. 
$ModelName.destroy_all → destroys all data inputs in the database leaving the schema untouched.  

