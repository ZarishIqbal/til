# Controllers

In Angular, a Controller is a JavaScript constructor function that is used to augment the Angular Scope.
When a Controller is attached to the DOM via the `ng-controller` directive, Angular will instantiate a new Controller object, using the specified Controller's constructor function. A new child scope will be available as an injectable parameter to the Controller's constructor function as $scope.

In general, a Controller shouldn't try to do too much. It should contain only the business logic needed for a single view.

```js
var myApp = angular.module("myApp", []);

myApp.controller("GreetingController", [
  "$scope",
  function ($scope) {
    $scope.greeting = "Hola!";
  },
]);
```

```html
<div ng-controller="GreetingController">{{ greeting }}</div>
```

### Use controllers to:

- Set up the initial state of the $scope object.
- Add behavior to the $scope object.

### Do not use controllers to:

- Manipulate DOM — Controllers should contain only business logic. Putting any presentation logic into Controllers significantly affects its testability. Angular has databinding for most cases and directives to encapsulate manual DOM manipulation.
- Format input — Use angular form controls instead.
- Filter output — Use angular filters instead.
- Share code or state across controllers — Use angular services instead.
- Manage the life-cycle of other components (for example, to create service instances).
