# Authentication

This brief tutorial explains how to hand-authenticate your Rails app using bcrypt.

## Workflow

### 1. Create a new Rails project

``` 
$ rails new authenticate
```

### 2. Create a User model

Make sure the model includes a username, email and password using password_digest.

``` 
$ rails g model User name email password_digest
```

### 3. Create a users controller


``` 
$ rails g controller users
```


### 4. Migrate your database

To ensure everything has been migrated to the database, run the following in the command line:


``` 
$ rake db:migrate
```

### 5. Add the bcrypt gem

Add the bcrypt gem to your Gemfile.


``` 
# Use ActiveModel has_secure_password
gem 'bcrypt', '~> 3.1.7'
```

Install bcrypt via your command line.

``` 
$ bundle
```

### 6. Include bcrypt in User model

Make sure bcrypt is included in the User model, exactly as shown below.


``` 
require 'bcrypt'
class User < ActiveRecord::Base
  has_secure_password
end
```

### 6. Adjust routes for signup

Add the following code to your routes.rb file to include the required routes for sign up.

``` 
get '/signup' => 'users#new'
post '/users' => 'users#create'
```

### 7. Add new and create methods 

Add this to the users controller you created earlier: app/controllers/users_controller.rb

``` 
class UsersController < ApplicationController

    def new
    end

    def create
    end   

end
```

### 8. Create a view file for signup form

Add a  new file new.html.erb to apps/views/users/. Include the signup form.


``` 
<h1>Signup for our super awesome app</h1>
<%= form_for :user, url: '/users' do |f| %>
	Name: <%= f.text_field :name %>
	Email: <%= f.text_field :email %>
	Password: <%= f.password_field :password %>
	Password Confirmation: <%= f.password_field :password_confirmation %>
<% end %>
```



