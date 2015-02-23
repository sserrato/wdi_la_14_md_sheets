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


### 12. Add create and destroy methods

Add the create and destroy methods to the sessions controller.

``` 
 def create
    user = User.find_by_email(params[:email])
    if user && user.authenticate(params[:password])
      session[:user_id] = user.id
      redirect_to '/'
    else
      redirect_to '/login'
    end
  end

  def destroy
    session[:user_id] = nil
    redirect_to '/login'
  end
```

### 13. Update application controller

Now you need to update the application controller to look up the user, find out if their logged in, and save the user object to a variable called @current_user.

``` 
class ApplicationController < ActionController::Base
  protect_from_forgery with: :exception

  def current_user
    @current_user ||= User.find(session[:user_id]) if session[:user_id]
  end
  helper_method :current_user

  def authorize
    redirect_to '/login' unless current_user
  end

end
```

### 14. Update the application view 

Adjust the application layout file to display the user's name if their logged in and include signup, log in and logout links. 

```
<!DOCTYPE html>
<html>
<head>
  <title>GifVault</title>
  <%= stylesheet_link_tag    "application", media: "all", "data-turbolinks-track" => true %>
  <%= javascript_include_tag "application", "data-turbolinks-track" => true %>
  <%= csrf_meta_tags %>
</head>
<body>

<% if current_user %>
  Signed in as <%= current_user.name %> | <%= link_to "Logout", '/logout' %>
<% else %>
  <%= link_to 'Login', '/login' %> | <%= link_to 'Signup', '/signup' %>
<% end %>

<%= yield %>

</body>
</html>
```

### 15. Extra: Before_Filter

If you want to secure any controller, to require a user to login before they can see this controller's actions, use the before_filter. Here is an example below.

```
class PostsController < ApplicationController

  before_filter :authorize

  def new
  end

  def create
  end
  
  def show
  end

  def index
  end

end
```

## Other Resources
* [Simple Authentication with Bcrypt](https://gist.github.com/thebucknerlife/10090014)
* [Railscast: Authentication from scratch](http://railscasts.com/episodes/250-authentication-from-scratch)
* [Method: has_secure_password](http://api.rubyonrails.org/classes/ActiveModel/SecurePassword/ClassMethods.html)