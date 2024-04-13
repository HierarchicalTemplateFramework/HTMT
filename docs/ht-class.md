# `ht-class`
The `ht-class` attribute in the HTMT (HyperText Markup Templating) system allows developers to dynamically apply CSS 
classes to HTML elements based on the evaluation of JSONPath expressions. This feature facilitates the responsive 
updating of the element's presentation according to changes in the data model.

## Syntax
The `ht-class` attribute uses a specific format to associate CSS classes with conditions. The attribute's name should 
start with `ht-class-` followed by the name of the class you want to conditionally apply. The value of the attribute is 
a JSONPath expression that evaluates to a boolean.

```html
<div ht-class-[class-name]="expression"></div>
```

- `[class-name]`: The CSS class to be applied conditionally.
- `expression`: A JSONPath expression that evaluates to `true` or `false`.

## Examples
### Applying a Single Class

Apply the `active` class to a list item if the current user is the selected user: 
```html
<li ht-class-active="$.id == $root.selectedUserId">John Doe</li>
```

In this example, the `active` class will be applied to the `<li>` element if the user's `id` matches `selectedUserId` 
from the global or root data context.

### Multiple Conditional Classes
Apply multiple classes based on different conditions: 
```html
<div 
    ht-class-active="$.status == 'active'"
    ht-class-admin="$.role == 'admin'"
    ht-class-highlight="$.highlight">
    User Details
</div>
```
Each class is conditionally applied based on the evaluation of its associated JSONPath expression.

## Best Practices
- **Clear Naming**: Use clear and descriptive names for your classes to ensure that the purpose of each class is easily understandable.
- **Minimize Complexity**: Keep the JSONPath expressions as simple as possible to reduce computational overhead and improve performance.
- **Reusable Logic**: If certain class conditions are used frequently across different parts of your application, consider abstracting these conditions into reusable components or helper functions.

## Compatibility
`ht-class` is implemented through JavaScript and depends on the evaluation of JSONPath expressions, which should be 
compatible with all modern browsers that support ECMAScript 2015 (ES6) and later. Ensure that your JavaScript 
implementation properly integrates with JSONPath libraries like `jsonpath-plus` to handle expression evaluation.

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution
guidelines.
