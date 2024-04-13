# `ht-switch`
The `ht-switch` attribute in the HTMT (HyperText Markup Templating) system is used to control the rendering of content 
based on the evaluation of an expression. It works similarly to a switch statement in programming languages, evaluating 
an expression and then rendering the child element that matches the result with a corresponding `ht-case`.

## Syntax
`ht-switch` is placed on a container element, and it contains one or more child elements with `ht-case` attributes. Each 
`ht-case` represents a possible value that the `ht-switch` expression can evaluate to.

```html
<div ht-switch="expression">
    <div ht-case="value1">Content for value1</div>
    <div ht-case="value2">Content for value2</div>
    <!-- More ht-case elements as needed -->
</div>
```
- `expression`: A JSONPath expression that the `ht-switch` evaluates.
- `value1, value2, ...`: Literal values or expressions that if matched by the `ht-switch` expression, will cause the corresponding `ht-case` content to be displayed.

## Examples
### User Role Based Content

Rendering different content based on the user's role: 
```html
<div ht-switch="$.user.role">
    <div ht-case="'admin'">
        <p>Admin Dashboard</p>
    </div>
    <div ht-case="'user'">
        <p>User Dashboard</p>
    </div>
    <div ht-case="'guest'">
        <p>Welcome, guest!</p>
    </div>
</div>
```

### Handling Default Cases
Using a default case when no specific match is found: 
```html
<div ht-switch="$.user.status">
    <div ht-case="'active'">
        <p>Your account is active.</p>
    </div>
    <div ht-case="'suspended'">
        <p>Your account is suspended.</p>
    </div>
    <div ht-case="default">
        <p>Status unknown. Please contact support.</p>
    </div>
</div>
```
## Best Practices
- **Default Case**: Always include a `ht-case="default"` to handle unexpected values or states gracefully.
- **Performance Considerations**: Keep the `ht-switch` expression as simple and efficient as possible, especially if the content being switched is complex or requires significant resources to render.
- **Expression Clarity**: Make sure that the JSONPath expression and the values in `ht-case` are clear and easy to understand. Use meaningful and descriptive values to enhance maintainability.

## Compatibility
`ht-switch` is implemented using JavaScript and relies on JSONPath for expression evaluation. It is compatible with all 
modern browsers that support ECMAScript 2015 (ES6) and later. Ensure that your implementation properly handles cases and 
defaults to maintain a consistent user experience across different browsers and platforms.

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution
guidelines.
