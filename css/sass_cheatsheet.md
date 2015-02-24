#Sass Cheatsheet

## Overview
This is an introduction to **Sass** - CSS with Superpowers!

###Intro
* Sass = Syntactically awesome style sheet
* Resource = [Sass Website](http://sass-lang.com/)
* Rails comes preloaded with Sass


###Workflow
You probably have already done these steps but if not, follow these when you start:

* $ bundle → ensure all gems are installed
* $ rake db:migrate → 
* $ rake db:seed → populate database with dummy data
* $ rails s → fire up server
* Then make edits in the defined .scss file in app > assets > stylesheets


###Nesting
  * Can nest selectors, one inside another
  * Saves you from longform; you can avoid rewriting the parent tag every time
  * To do so, input them inside the CSS selector tag, example below
  * Resource: [Sass Beginners](http://thesassway.com/beginner/the-inception-rule)

		body {
  			background-image: url("starrynight.jpg");
  			background-repeat: no-repeat;
  			background-size: cover;
  			text-align: center; 	
  				.main {
    				background-color: white;
    				margin: auto 0;
  				}
  		}
  	
  	
 
###Variables
 * Don’t have to be defined at the top of stylesheet, but makes for better organization
 * To get the variables to flow to other stylesheets, define them in application.css
 * Only has to be defined/changed once and then will be adjusted in multiple areas
 * Example below:
 
		$basewidth: 600px;
		$maincolor: #859DC6;
		$mainfont: cursive;

		body {
 		 background-image: url("starrynight.jpg");
 		 background-repeat: no-repeat;
  		background-size: cover;
  		text-align: center;

  			.main {
   				 background-color: white;
    			 margin: auto 0;
    			width: $basewidth;
   				font-family: $mainfont;
  			}

 			.painting {
    			background-color: $maincolor;
    			color: $maincolor;
  			}
		}
		
		
###Operators
* Can perform logic in CSS
* Example: width: $basewidth / 960px *100%;


###Mixins
* A special kind of multiple inheritance that you use when you want to provide optional features for a class
* Example below: 

		@mixin border-radius($radius) {
 		 -webkit-border-radius: $radius;
 		 -moz-border-radius: $radius;
 		 -ms-border-radius: $radius;
 		 border-radius: $radius;
		}

 		.main {
   		 	background-color: white;
    		margin: auto 0;
   			width: $basewidth / 960px *100%;
    		font-family: $mainfont;
    		@include border-radius(15px);
 		}
 		
###Darken/Lighten
* To darken: background-color: darken($maincolor, 50%);
* To lighten: color: lighten($maincolor, 20%);
 	

###@import
* Can import partials, special fonts, etc.
* Example: @import
  * url(http://fonts.googleapis.com/css?family=Covered+By+Your+Grace);


###Inheritance / @extend
* Let's you share a set of properties from one CSS selector to another
* Example:

		.border-party {
			border: 2px solid yellow;
		}

		.details {
			@extend .border-party;
		}
		
		








