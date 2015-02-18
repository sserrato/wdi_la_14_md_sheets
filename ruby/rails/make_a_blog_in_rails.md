#Make a Blog In Rails

In this document we're going to go through the steps of making a simple Rails blog. 

###Data Modeling

####Users
id | integer <br>
email | string <br>

###Create the MVC of the App

```rails new brain_fog_blog -T<br>
cd brain_fog_blog<br>
rails g model User email password_digest<br>
rails g controller users index new create <br>
rails g controller sessions new create destroy<br>
subl . 

rails g model Post title post_text:text user:belongs_to <br>
rails g controller posts index new create destroy show <br>
rails g model Post title post_text:text user:belongs_to<br>
rails g controller posts index new create destroy show```

Then modify user.rb to: `has_many:posts`.