##BOOTSTRAP CHEAT SHEET

* Index
* Intro
* Workflow
* Grids
* Typography / Glyphicons / Buttons
* Modals & Dropdowns
* Image Carousels
* Nav Bar
* Tables & Breadcrumbs
* Forms
* Intro
A CSS framework
Originated internally at Twitter
Made open source and available to the public
Allows you to style quickly and reduce the workload (convention over configuration)
http://getbootstrap.com/2.3.2/
https://github.com/twbs/bootstrap-sass

Workflow
Create new Rails app
Add Bootstrap gem to gemfile: gem 'bootstrap-sass', '~> 3.2.0'

```bash
$ bundle
```

In app > assets > stylesheets > application.css, add @import 'bootstrap';
Rename application.css to application.css.scss
Add Bootstrap Jquery script & Glyphicon library to app > views > layouts > application.html.erb

```html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<link href="//netdna.bootstrapcdn.com/bootstrap/3.0.0/css/bootstrap-glyphicons.css" rel="stylesheet">
```

Grids
Bootstrap offers a responsive grid format that uses 12 columns

Typography / Glyphicons / Buttons
http://getbootstrap.com/css/#type
http://getbootstrap.com/components/#glyphicons
http://getbootstrap.com/css/#buttons

Modals & Dropdowns
http://getbootstrap.com/javascript/#modals
http://getbootstrap.com/javascript/#dropdowns

Image Carousels
http://getbootstrap.com/javascript/#carousel

Nav Bar
http://getbootstrap.com/components/#nav

Tables & Breadcrumbs
http://getbootstrap.com/css/#tables
http://getbootstrap.com/components/#breadcrumbs

Forms
http://getbootstrap.com/css/#forms
