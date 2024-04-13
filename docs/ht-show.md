# `ht-show`
The `ht-show` attribute in the HTMT (HyperText Markup Templating) system is used to conditionally display HTML elements 
based on specific data conditions. By evaluating a JSONPath expression, `ht-show` determines whether an element should be 
visible, making it a powerful tool for creating interactive and data-driven user interfaces.

## Syntax
The `ht-show` attribute can be added to any HTML element. The value of this attribute is a JSONPath expression that 
evaluates to a boolean. If the expression evaluates to `true`, the element is displayed; if `false`, the element is hidden.
```html
<div ht-show="expression"></div>
```
- `expression`: A JSONPath expression that determines the visibility of the element.

## Examples
### Basic Visibility Control
Displaying a welcome message only if a user is logged in: 
```html
<div ht-show="$.user.isLoggedIn">
    Welcome back, user!
</div>
```
### Complex Conditional Display
Displaying an element based on multiple conditions, such as showing a special offer only to users who are subscribers 
and have been members for more than a year: 
```html
<div ht-show="$.user.isSubscriber && $.user.membershipDuration > 12">
    Special offer just for you!
</div>
```
## Best Practices
- **Use Clear Expressions**: Ensure that your JSONPath expressions are clear and maintainable. Complex conditions should be well-documented or abstracted into simpler, named conditions if possible.
- **Optimize Data Bindings**: Optimize how data updates affect visibility. Frequently evaluated expressions or those triggered by high-frequency data changes should be handled efficiently to avoid performance issues.
- **Accessibility Considerations**: Manage how hidden elements are treated by screen readers and other assistive technologies. Use appropriate `aria` attributes to ensure that the visibility state is communicated to all users.

## Compatibility
`ht-show` is implemented through JavaScript and depends on JSONPath for expression evaluation. It is compatible with all 
modern web browsers that support ECMAScript 2015 (ES6) and later. It is recommended to ensure that your JavaScript code 
handling `ht-show` degrades gracefully in environments where JavaScript might be disabled.

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution
guidelines.
