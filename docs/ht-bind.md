# `ht-bind`

The `ht-bind` attribute binds data from your JSON model directly to the HTML element's content or specific attributes.

## Syntax
```html
<element ht-bind="expression">`
```
- `expression`: A JSONPath expression that specifies which part of the model to bind.

## Example

```html
<div ht-bind="$.user.name">This will be replaced with the user's name.</div>
```

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution
guidelines.
