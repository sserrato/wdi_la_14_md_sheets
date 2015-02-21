# Useful code snippets

#### Find a specific model based on id number
```ruby
Model.find(id)
```
#### Find a specific model instance that passes whatever the parameters of the id are
```ruby
Model.find(params[:id])
```
#### Using 'where' to find a particular record 
<p>You need the .first to only get one record, otherwise you'll get an array of records (even if it's an empty array)
```ruby
@groceries = Grocery.where(is_purchased: false).first
```
#### Embedded Ruby that allows you to see parameters of the view.
```ruby
<%= params.inspect %> →   
```
#### To add ‘belongs_to’ automatically in the model when generating it
```ruby
$rails g model order item quantity:integer address user:belongs_to
rails g model order item quantity:integer address user:references (equivalent to line above)
```
#### To dynamically add numbers to a loop (and/or find out current index)
<p>  This will interate through all the posts in @post1 and display the index number for each post. We added +1 to index because so our first displayed number will start at 1 and not 0, assuming we're pulling the latest posts.
```ruby
<% @post1.each_with_index do |post, index|%>
	<%= (index+1) %>
```

#### More examples.
```ruby

```
#### More examples.
```ruby

```
