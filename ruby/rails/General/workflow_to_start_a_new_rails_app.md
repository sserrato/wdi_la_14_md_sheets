#Workflow to Start a New Rails App
[Index](https://github.com/blaisethomas/wdi_la_14_md_sheets)
--- 
2. Terminal - **cd into your rails projects folder**
3. Terminal - **mkdir projectname**
4. Terminal - **cd projectname**
5. Terminal - **rails new filename** (filename should be singular and start with a lowercase letter)
6. In your Gemfile turn off the turbolinks and gem file 
7. Terminal - **bundle** (remove the gems)
8. Terminal - **rails g Modelname** (the Modelname should also be singular but start with a capital letter)
9. Terminal - **rails g controller controllernames** (the controllername should be lowercase and plural)
10. Next - you will need to add all of the requires methods in the controller and the views
11. Terminal - **rails g controller name index new show edit** (this create the views and controller methods)

###Views
1. index.html.erb 
2. new.html.erb 
3. edit.html.erb
4. show.html.erb
5. _form.html.erb 

###Controller Methods
1. def index
2. def create
3. def edit
4. def update
5. def show
6. def destroy

###Routes
1. Next, you should create the required routes in the routes.rb file
2. (example) 

```Rails.application.routes.draw do
  resources :pastries
  get 'beverages' => 'beverages#index'
  get 'beverages/new' => 'beverages#new'
  post 'beverages/' => 'beverages#create'
  get 'beverages/:id/edit' => 'beverages#edit'
  patch 'beverages/:id/' => 'beverages#update'
  get 'beverages/:id' => 'beverages#show', as: :beverage
  delete 'beverages/:id' => 'beverages#destroy'```
  
  3. Next, Terminal - **rake routes** (returns all open routes)
  4. Finally, populate your local database with the data you have built by -- Terminal - **rake db:migrate**



