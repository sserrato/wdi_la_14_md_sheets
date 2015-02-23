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

Add a  new file new.html.erb to apps/views/users/. Include the signup form. Any time a new user is created, it will pass through this view.


``` 
<h1>Signup for our super awesome app</h1>
<%= form_for :user, url: '/users' do |f| %>
	Name: <%= f.text_field :name %>
	Email: <%= f.text_field :email %>
	Password: <%= f.password_field :password %>
	Password Confirmation: <%= f.password_field :password_confirmation %>
<% end %>
```

### 9. Add logic to create method on users controller

To ensure the new user creation action occurs, add the following the create method in the users controller.

``` 
class UsersController < ApplicationController

  def new
  end

  def create
    user = User.new(user_params)
    if user.save
      session[:user_id] = user.id
      redirect_to '/'
    else
      redirect_to '/signup'
    end
  end

private

  def user_params
    params.require(:user).permit(:name, :email, :password, :password_confirmation)
  end
end
```
Awesome, you now have a working signup view and method! Now let's move on to log in.

### 10. Create a sessions controller

Your sessions controller is going to be where you create the login and logout methods. 

``` 
$ rails g controller sessions
```

Every time a session is created, it means a user is logged in. Every time a session is destroyed, a user is logged out.

Add the following methods to your sessions controller.

``` 
class SessionsController < ApplicationController

  def new
  end

  def create
  end

  def destroy
  end

end
```

### 10. Create a view form for the login

Add a  new file new.html.erb to apps/views/sessions/. Include the login form. 

``` 
<h1>Login</h1>

<%= form_tag '/login' do %>

  Email: <%= text_field_tag :email %>
  Password: <%= password_field_tag :password %>
  <%= submit_tag "Submit" %>

<% end %>
```

### 11. Adjust routes for login

Add the following code to your routes.rb file to include the required routes for logging in.

``` 
get '/login' => 'sessions#new'
post '/login' => 'sessions#create'
get '/logout' => 'sessions#destroy'
```


