# Services

Angular services are substitutable objects that are wired together using dependency injection (DI). You can use services to organize and share code across your app.

Angular services are:

- Lazily instantiated – Angular only instantiates a service when an application component depends on it.
- Singletons – Each component dependent on a service gets a reference to the single instance generated by the service factory.

```js
angular
  .module("myServiceModule", [])
  .controller("MyController", [
    "$scope",
    "notify",
    function ($scope, notify) {
      $scope.callNotify = function (msg) {
        notify(msg);
      };
    },
  ])
  .factory("notify", [
    "$window",
    function (win) {
      var msgs = [];
      return function (msg) {
        msgs.push(msg);
        if (msgs.length == 3) {
          win.alert(msgs.join("\n"));
          msgs = [];
        }
      };
    },
  ]);
```

```html
<div id="simple" ng-controller="MyController">
  <p>Let's try this simple notify service, injected into the controller...</p>
  <input ng-init="message='test'" ng-model="message" />
  <button ng-click="callNotify(message);">NOTIFY</button>
  <p>(you have to click 3 times to see an alert)</p>
</div>
```