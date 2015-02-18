#AngularJS Forms

[INDEX](git@github.com:blaisethomas/wdi_la_14_md_sheets.git)

An AngularJS form is a collection of input controls.

The key directive in understanding two-way data-binding is ngModel. The ngModel directive provides the two-way data-binding by synchronizing the model to the view, as well as view to the model. In addition it provides an API for other directives to augment its behavior.

```

  <div ng-controller="ExampleController">
  
    <form novalidate class="simple-form">
    
      Name: <input type="text" ng-model="user.name" /><br />
      
      E-mail: <input type="email" ng-model="user.email" /><br />
      
      Gender: <input type="radio" ng-model="user.gender" value="male" />male
              <input type="radio"   ng-model="user.gender"   value="female" />female<br />
      
      
      <input type="button"  ng-click="reset()"       value="Reset"  />
      <input type="submit"  ng-click="update(user)"  value="Save"   />
      
  </form>

</div>

```

```

	angular.module('formExample', []).controller('ExampleController', ['$scope', function($scope) {
      
	  $scope.master = {};
	  
	  $scope.update = function(user) {
	    $scope.master = angular.copy(user);
	  };

	  $scope.reset = function() {
	    $scope.user = angular.copy($scope.master);
	  };

	  $scope.reset();
	}]);
	
```

This is what the above code outputs:
<html>
<div ng-controller="ExampleController">
  <form novalidate class="simple-form">
    Name: <input type="text" ng-model="user.name" /><br />
    E-mail: <input type="email" ng-model="user.email" /><br />
    Gender: <input type="radio" ng-model="user.gender" value="male" />male
    <input type="radio" ng-model="user.gender" value="female" />female<br />
    <input type="button" ng-click="reset()" value="Reset" />
    <input type="submit" ng-click="update(user)" value="Save" />
  </form>
</div>

<script>
  angular.module('formExample', [])
    .controller('ExampleController', ['$scope', function($scope) {
      $scope.master = {};

      $scope.update = function(user) {
        $scope.master = angular.copy(user);
      };

      $scope.reset = function() {
        $scope.user = angular.copy($scope.master);
      };

      $scope.reset();
    }]);
</script>
</html>

<br>
<hr>
<br>

+ The **ng-app** directive defines the AngularJS application.
+ The **ng-controller** directive defines the application controller.
+ The **ng-model** directive binds two input elements to the user object in the model.
+ The **formController()** function sets initial values to the master object, and invokes the reset() method.
+ The **reset()** method sets the user object equal to the master object.
+ The **ng-click** directive invokes the reset() method, only if the button is clicked.
+ The **novalidate** attribute is not needed for this application, but normally you will use it in AngularJS forms, to override standard HTML5 validation.