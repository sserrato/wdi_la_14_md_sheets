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
#### More examples.
```ruby

```
#### More examples.
```ruby

```
