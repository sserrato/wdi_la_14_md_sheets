# Authentication

This brief tutorial explains how to hand-authenticate your Rails app using bcrypt.

## Workflow

### 1. Create a new Rails project

``` $ rails new authenticate
```

### 2. Create a User model

Make sure the model includes a username, email and password using password_digest.

``` $ rails g model User name email password_diggest
```

### 3. Create a users controller


``` $ rails g controller users
```


### 4. Migrate your database

To ensure everything has been migrated to the database, run the following in the command line:


``` $ rake db:migrate
```

### 5. Add the bcrypt gem

Add the bcrypt gem to your Gemfile.


``` # Use ActiveModel has_secure_password
gem 'bcrypt', '~> 3.1.7'
```

Install bcrypt via your command line.

``` $ bundle
```


