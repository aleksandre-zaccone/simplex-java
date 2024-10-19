# Angular

Create Angular project

ng version
ng new angularDemo001
ng generate module MODULE_NAME


Angular Module



Angular Decorators
- @NgModule to define a module.
- @Component to define components.
- @Injectable to define services.
- @Input and @Output to define properties, etc.


# Angular Component

# Angular binding Types
- Interpolation -  {{username}} - component field's value into View, when wee need to bind a value directly to the text content of an element. 
- Property Binding - <img [src]="imageUrl"> - bind values of the component to HTML element , when you need to bind data to HTML element properties or attributes, such as setting a button to be disabled, binding an image’s src, or controlling styles dynamically.    
- Attribute Binding - <th [attr.colspan] = "ColumnSpan> {{pageHeader}} </th> - bind component field value to HTML attribute
- Class Binding - used to add or remove classes to and from the HTML elements
- Style Binding - used to set the style in HTML elements
- Event Binding - bind dom event to component method
- Two-way binding  - used in the input type filed or any form element where the user type or provide any value or 
change any control value on the one side and on the other side, the same automatically updated into the component 
variables and vice-versa is also true.

Example
```html
<div>
    <p>Name : <input  type="text" [(ngModel)]="userName" ></p>
    <br>
    <p>You entered : {{ userName }} </p>
  </div>

```

# Angular Form
https://angular.dev/guide/forms#choosing-an-approach
template-driven forms - simple. uses html val;idations
reactive forms - advanced In the reactive form, .



# Angular events            