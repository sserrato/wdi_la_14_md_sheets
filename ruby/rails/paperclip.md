#Installing Paperclip into a Rails app

####This markdown will walk you through the steps of installing the paperclip gem into your rails app and upload to amazon s3 for heroku deployment

# Adding Paperclip

## Step 0 - Install Imagemagick
at your cli type ...

	brew install imagemagick

then...

## Step 1 - Add more Gems
inside your gemfile...

- gem "paperclip", "~> 4.2"

then from the common line run

	bundle install


#Add avatar to existing user model path
<br>
`You must have a User model present in order to add the avatar column to the User table`

In our user.rb file we add the following:

```
class User < ActiveRecord::Base
  has_attached_file :avatar, :styles => { 
  	:medium => "300x300>", 
  	:thumb => "100x100>" }, 
  	:default_url => "/images/:style/missing.png"
  
  validates_attachment_content_type :avatar, :content_type => /\Aimage\/.*\Z/
end
```

### Now we create the migration to add the avatar column to our User model's schema:



```
rails generate paperclip user avatar
```

### We need to get those migrations in our db with a little 
```
rake db:migrate
```
(Check your db schema and confirm that 4 avatar properties have been added to your User table)

###In our user controller we need to permit the avatar field in our user params:

```
def user_params
   params.require(:user).permit(:email, :avatar)
end
```

###Now we add the avatar field to our new and edit user forms like so:

```
<%= f.file_field :avatar %>
```

and you're good to go!!

####You can render the image using the different size attributes we defined in our User model:

```
<%= image_tag @user.avatar.url %>
<%= image_tag @user.avatar.url(:medium) %>
<%= image_tag @user.avatar.url(:thumb) %>
```

<br>

#The "Many Photos Path"

###Model(s)

Let's create a photo model...

```
rails g model Photo photo_date:date user:references
```
the `user:references` is not required but if your user has many photos this would be one option to start that relationship

and now we add our `has_attached_file` and specify the sizes we want to our new Photo model, it should look like this:

<br>
**models/photo.rb**

	class Photo
		belongs_to :user
		
		has_attached_file :image, 
	   :styles => {
	      :original => ['1920x1680>', :jpg],
	      :small    => ['100x100#',   :jpg],
	      :medium   => ['250x250',    :jpg],
	      :large    => ['500x500>',   :jpg]
	    }
		validates_attachment_content_type :image, content_type: ["image/jpg", "image/jpeg", "image/png", "image/gif"]
	end
	

(`belongs_to :user` only if that relationship applies to your app)
***
A note from Paperclip on the "validates_attachment_content_type" part:

You should ensure that you validate files to be only those MIME types you explicitly want to support. If you don't, you could be open to XSS attacks if a user uploads a file with a malicious HTML payload.

If you're only interested in images, restrict your allowed content_types to image-y ones:

validates_attachment :avatar,
  :content_type => { :content_type => ["image/jpeg", "image/gif", "image/png"] }
  ***
	
**and edit model/user.rb with our has_many if that relationship applies:**

	class User
	
	  has_many :photos
	
	end
	

###Let's use the rails g command our paperclip gem gives us to add our 4 image fields to our photo model schema:

```
rails generate paperclip photo image
```
followed by a
```
rake db:migrate
```

when successfully completing the migrations your photo model's schema should look something like this:

```
create_table "photos", force: true do |t|
    t.date     "photo_date"
    t.integer  "user_id"
    t.datetime "created_at",         null: false
    t.datetime "updated_at",         null: false
    t.string   "image_file_name"
    t.string   "image_content_type"
    t.integer  "image_file_size"
    t.datetime "image_updated_at"
  end
```


##Now lets setup our photos controller

`rails g controller photos`

...and add the following code to your new photos controller file: 
`note the create controller action is attaching a photo to current_user, you must have setup current_user in your application controller prior for this attachment to work, otherwise use the standard create method`

 **photos_controller.rb**

	class PhotosController < ApplicationController
	  def index
	  	@photos = Photo.all
	  end
	  def new
	  	@photo =Photo.new
	  end
	  def create
	  	# Find our user that we should attach to
	    #@photo = current_user.photos.new(photo_params)
	    #or the standard create:
	    @photo = Photo.create(photo_params)
	    if @photo.save
	      redirect_to photos_path
	    else
	      render 'new'
	    end
	  end
	
	  def show
	  	
	  end
	
	  def photo_params
	    params.require(:photo).permit(:image, :photo_date)
	  end
	end
	

####Lets add some photo routes to our `config>routes.rb` with:
```
resources :photos
```

and a sample new photo form:
<br>
 (note you'll want to add the user to this form_for if you're attaching photos to someone)

```
	<h1>Photos#new</h1>
	<p>Find me in app/views/photos/new.html.erb</p>
	
	<%= form_for(@photo) do |f| %>
	
	  <div class="field">
	    <%= f.label :photo_date %><br>
	    <%= f.date_field :photo_date %>
	  </div>
	
	  <div class="field">
	    <%= f.label :image %><br>
	    <%= f.file_field :image %>
	  </div>
	
	  <div class="actions">
	    <%= f.submit %>
	  </div>
	<% end %>

```


And that's it!


#play

####If you're attaching photos to another model like user here is a sample of how you might render the photos belonging to someone
in our views/users/**index.html.erb**

remember that small medium large business we did in the photo.rb model...well that lets us save various image sizes. so now we can have our view do this

	<p>I'm a place holder page. I'm located in <%= users_path %> /index.html.erb </p>
	<% if current_user != nil %>
		<% @users.each do |u| %>
			<div class="user_box"><h1><%= u.email %></h1>
				<% u.photos.each do |p| %>
					<%= image_tag p.image.url(:original) %><br />
					<%= image_tag p.image.url(:small) %><br />
					<%= image_tag p.image.url(:medium) %><br />
					<%= image_tag p.image.url(:large) %><br />
				<% end %>
			</div>
		<% end %>
	<% end %>
	


 

#Sources

paperclip - [https://github.com/thoughtbot/paperclip](https://github.com/thoughtbot/paperclip)