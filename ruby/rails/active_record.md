#Active Record

##### Connects your app to the database; it maps objects to database table record sets.

###### It is an ORM (Object Relation Mapping).*


###### Check Out Grant’s Markdown on ORM 



###Using Command Line For Migrations



```bash
$ rails g migration AddIsGroundToBeans is_ground:boolean
```

```bash
$ rails g migration AddStuffToBeans lat:float lon:float address
```

####Useful code snippets

#####ruby

1. **Model.find(id)** → find a specific model based on id #

2. **Model.find(params[:id])** → find a specific model instance that passes whatever the parameters of the id are

3. **<%= params.inspect %>** → embedded Ruby that allows you to see parameters of the view.



