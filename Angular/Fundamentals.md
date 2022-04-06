# Angular

Development platforn built on `TypeScript`.
It includes

- A component-based framework for building scalable web applications
- A collection of well-integrated libraries that cover a wide variety of features including routing, forms management, client-server communication, and more
- A suite of developer tools to help you develop, build, test, and update your code

## Essentials

### Components

A component consists of 3 things:

- _A component class_ that handles data and functionality
- _An HTML template_ that determines the UI
- _Component-specific styles_ that define the look and feel

```ts
import { Component } from "@angular/core";

@Component({
  selector: "hello-world",
  template: `
    <h2>Hello World</h2>
    <p>This is my first component!</p>
  `,
})
export class HelloWorldComponent {
  // The code in this class drives the component's behavior.
}
```

> The `@Component()` decorator specifies a `CSS selector`, `an HTML template` and optional set of CSS styles.

> HTML elements in your template that match this selector become instances of the component.

To use this component, you write the following in a template:

```html
<hello-world></hello-world>
```

When Angular renders this component, the resulting DOM looks like this:

```html
<hello-world>
  <h2>Hello World</h2>
  <p>This is my first component!</p>
</hello-world>
```

### Templates

Every component has an HTML template that declares how that component renders. You define this template either inline or by file path.

Inserting dynamic text:

```html
<p>{{ message }}</p>
```

The values for message comes from the component class:

```ts
import { Component } from "@angular/core";

@Component({
  selector: "hello-world-interpolation",
  templateUrl: "./hello-world-interpolation.component.html",
})
export class HelloWorldInterpolationComponent {
  message = "Hello, World!";
}
```

When the application loads the user sees the following:

```html
<p>Hello, World!</p>
```

The following is a combines example of Interpolation, Property Binding and Event Binding within an Angular template:

```ts
import { Component } from "@angular/core";

@Component({
  selector: "hello-world-bindings",
  templateUrl: "./hello-world-bindings.component.html",
})
export class HelloWorldBindingsComponent {
  fontColor = "blue";
  sayHelloId = 1;
  canClick = false;
  message = "Hello, World";

  sayMessage() {
    alert(this.message);
  }
}
```

Angular also supports property bindings, to help set values for properties and attributes of HTML elements and pass values to your application's presentation logic.

```html
<p [id]="sayHelloId" [style.color]="fontColor">
  You can set my color in the component!
</p>
```

_Notice the use of the square brackets--that syntax indicates that you're binding the property or attribute to a value in the component class._

You declare an event listener by specifying the event name in parentheses:

```html
<button type="button" [disabled]="canClick" (click)="sayMessage()">
  Trigger alert message
</button>
```

We can add additional functionalities using directives. The most popular directives are `*ngFor` and `*ngIf`

Example of `*ngIf` directive.

```ts
import { Component } from "@angular/core";

@Component({
  selector: "hello-world-ngif",
  templateUrl: "./hello-world-ngif.component.html",
})
export class HelloWorldNgIfComponent {
  message = "I'm read only!";
  canEdit = false;

  onEditClick() {
    this.canEdit = !this.canEdit;
    if (this.canEdit) {
      this.message = "You can edit me!";
    } else {
      this.message = "I'm read only!";
    }
  }
}
```

```html
<h2>Hello World: ngIf!</h2>

<button type="button" (click)="onEditClick()">Make text editable!</button>

<div *ngIf="canEdit; else noEdit">
  <p>You can edit the following paragraph.</p>
</div>

<ng-template #noEdit>
  <p>The following paragraph is read only. Try clicking the button!</p>
</ng-template>

<p [contentEditable]="canEdit">{{ message }}</p>
```
