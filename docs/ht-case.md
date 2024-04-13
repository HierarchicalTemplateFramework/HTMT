# `ht-case`
The `ht-case` attribute in the HTMT (HyperText Markup Templating) system is used in conjunction with the `ht-switch` 
attribute to conditionally render content based on the evaluation of an expression. `ht-case` specifies the content that 
should be displayed when the ht-switch expression matches a specific value.

## Syntax
The `ht-case` attribute is used within an element that is a direct child of an element with an `ht-switch` attribute. It 
specifies the value that, when matched by the `ht-switch` expression, causes the element to be rendered.
```html
<div ht-switch="expression">
    <div ht-case="value">Content for the case</div>
</div>
```
- `expression`: A JSONPath expression evaluated by the `ht-switch`.
- `value`: The specific value that the `ht-switch` expression must match for this `ht-case` to be rendered.

## Examples
### Basic Usage
In a scenario where user roles determine content visibility: 
```html
<div ht-switch="$.user.role">
    <div ht-case="'admin'">Admin Panel</div>
    <div ht-case="'user'">User Dashboard</div>
    <div ht-case="'guest'">Welcome, guest!</div>
</div>
```

### Default Case
You can also specify a default case using `ht-case="default"`, which renders if no other case matches: 
```html
<div ht-switch="$.user.role">
    <div ht-case="'admin'">Admin Panel</div>
    <div ht-case="'user'">User Dashboard</div>
    <div ht-case="default">Default content for other roles</div>
</div>
```

## Best Practices
- **Matching Values**: Ensure that the value in `ht-case` exactly matches possible outcomes of the `ht-switch` expression, considering data types (string vs. number vs. boolean).
- **Use of Default Case**: Always provide a `ht-case="default"` as a fallback to handle unexpected or undefined values gracefully.
- **Performance Considerations**: Minimize the complexity of the `ht-switch` expression to enhance performance, especially in scenarios where the switch block is part of a larger, dynamically updated section.

## Compatibility
`ht-case` relies on standard HTML and JavaScript capabilities and should work across all modern browsers that support 
ECMAScript 2015 (ES6) and later. Ensure your application handles edge cases and browser-specific behaviors, particularly 
in how expressions are evaluated and content is rendered.

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution
guidelines.
