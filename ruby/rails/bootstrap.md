# How To Add Twitter Bootstrap To Your App

![image](http://logonoid.com/images/bootstrap-logo.png./pic/pic1s.png =150x)


## Overview

Follow these steps to **Bootstrapify** your Rails App.


### Step 1 
Add Bootstrap Gem to your gemfile:

```
gem 'bootstrap-sass', '~> 3.2.0'
```

***Check your ticks!***

### Step 2

From Command Line:

```
Bundle Install
```

### Step 3

Start Server

2. Rails S



### Step 4

Within the App > Assets > Javascripts > Application.js

Add:

```
//= require bootstrap
```

to directives ***in this order:***

```
//= require jquery
//= require jquery_ujs
//= require turbolinks
//= require bootstrap
//= require_tree .

```

### Step 5

Within the App > Assets > Stylesheets > Application.css

Add to bottom of file:

```
@import 'bootstrap';
```


Then rename file Application.css***.scss***


### Step 6

Within the Apps > Views > Layouts > Application.html.erb

Add these scripts/links to the HEAD:


```
 <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
 
<link href="//netdna.bootstrapcdn.com/bootstrap/3.0.0/css/bootstrap-glyphicons.css" rel="stylesheet">
```

The ***1st*** enables jquery animations

The ***2nd*** enables the glyphicon library

### Bootstrap Away!

#getbootstrap.com

