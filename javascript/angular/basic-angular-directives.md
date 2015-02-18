#Basic AngularJS Directives

Angular directives allow the developer to specify custom and reusable HTML-like elements and attributes.

##Some Useful Directives

####Main Application

+ **ng-app** – declares the root element of the AngularJS application (put ng-app in the tag of the element where the model is called)

+ **ng-controller** – defines the application controller (specifies a JavaScript controller class that evaluates HTML expressions)

####Behavior

+ **ng-click** – specifies behavior when the HTML element is clicked

####Variable binding

+ **ng-bind** – replaces the text content of the DOM element with the value of the given expression. For example, ```<span ng-bind="name"></span>``` will display the value of ‘name’ inside the span element. Any changes to the variable ‘name’ in the application's scope are reflected instantly in the DOM.

+ **ng-model** – two-way binding between the view and the scope (sends and receives information to/from the DOM element)

####CSS

+ **ng-class** – allows class attributes to be dynamically loaded, based on a boolean value

+ **ng-style** – adds/adjusts CSS style to DOM elements

+ **ng-show/ng-hide** – conditionally show or hide an element, depending on the value of a boolean expression; show and hide is achieved by setting the CSS display style

####Arrays

+ **ng-repeat** – instantiate an element once per item from a collection (array); each template instance gets its own scope, where the given loop variable is set to the current collection item, and $index is set to the item index or key. For example, `<div ng-repeat="(key, value) in myObj"> ... </div>`