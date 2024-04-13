# `ht-loop`
The `ht-loop` attribute is used to iterate over an array or collection in your JSON data, rendering the enclosed 
HTML block for each item in the array. This attribute simplifies the process of generating dynamic lists and tables in 
your HTML based on data from your model.

## Syntax
The `ht-loop` attribute is placed on an HTML element that acts as the container for each iteration of the loop.

```html
<div ht-loop="expression">
    <!-- Content to repeat for each item -->
</div>
```
- `expression`: A JSONPath expression that specifies the array or collection to iterate over.

## Parameters
- `expression`: This must evaluate to an array or iterable collection in your JSON data. The expression uses JSONPath syntax, allowing for complex data navigation and filtering.

## Example Usage
### Basic Loop
Iterating over a list of users and displaying their names and emails: 
```html
<ul ht-loop="$.users[*]">
    <li>
        Name: <span ht-bind="$.name"></span>,
        Email: <span ht-bind="$.email"></span>
    </li>
</ul>
```

### Conditional Rendering Inside Loop
Displaying items only if they meet a certain condition, such as being active users: 

```html
<div ht-loop="$.users[?(@.isActive)]">
    <div>
        <h3 ht-bind="$.name"></h3>
        <p ht-bind="$.email"></p>
    </div>
</div>
```

## Best Practices
- **Preprocessing Data**: If your data needs manipulation before rendering (e.g., sorting or filtering), consider preprocessing it in your JavaScript before applying the loop. This approach can simplify your templates and improve performance.
- **Minimize DOM Access**: Since ht-loop creates multiple DOM elements, ensure that the contents within the loop are optimized to minimize browser reflow and repaint costs.
- **Keyed Elements**: If your rendering involves updating the list frequently (e.g., adding or removing items), consider implementing a mechanism to key each element uniquely based on the data to optimize updates and prevent unnecessary DOM manipulations.

## Compatibility
`ht-loop` is implemented through JavaScript and is compatible with all modern browsers that support ECMAScript 2015 (ES6) 
and later. Ensure that your JavaScript environment or framework supports JSONPath expressions if you use advanced 
JSONPath features within the loop.

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution
guidelines.
