# Root-Level Data Access in HTMT - `Rooting`
The HTMT (HyperText Markup Templating) system enables templating features that can access data directly from the root of
the JSON data structure. This is facilitated by attributes prefixed with `ht-root-`, which allow elements to bypass local
data scopes and bind directly to data defined at the root level.

## Usage
Root-level data access is essential for components that need to reference global or shared data irrespective of their
position within the data hierarchy. The `ht-root-` prefix can be used with various attributes to achieve this functionality:

## Attributes with Root Access
| Attribute                        | Description                                                                     |
|----------------------------------|---------------------------------------------------------------------------------|
| `ht-root-bind`                   | Binds element content or specific attributes directly to root-level data.       |
| `ht-root-attr-[attribute-name]`  | Sets an HTML attribute based on a root-level data property.                     |
| `ht-root-class-[class-name]`     | Conditionally applies a CSS class based on a root-level data evaluation.        |
| `ht-root-show` / `ht-root-hide`  | Controls element visibility based on root-level data conditions.                |
| `ht-root-loop`                   | Iterates over a collection defined at the root of the JSON data.                |
| `ht-root-switch`                 | Evaluates a root-level expression to render content conditionally.              |
| `ht-root-template`               | Specifies a block to be reused, which is instantiated based on root-level data. |

## Example Usage
Applying a class based on a user's role defined at the root of the data:
```html
<div ht-root-class-admin="$.user.role == 'admin'">
    Admin content here.
</div>
```

Displaying user information regardless of local data context:
```html
<div ht-root-bind="$.user.name">User's Name</div>
```

## Best Practices
- **Clear Documentation**: Maintain clear documentation of how root-level data is structured to ensure that `ht-root-` attributes are used correctly.
- **Avoid Overuse**: Use root-level data access judiciously to avoid bypassing structured data scopes unnecessarily, which can lead to less maintainable templates.

## Compatibility
Attributes prefixed with `ht-root-` are implemented in JavaScript and depend on the JSONPath syntax for data access. They
are compatible with modern browsers that support ECMAScript 2015 (ES6) and later.

## Attribute Precedence
In HTMT, certain scenarios require clear guidelines regarding attribute precedence to avoid conflicts and ensure
predictable rendering behavior. Specifically, when both `ht-root-bind` and `ht-bind` are used on the same element, there
are rules that determine which attribute takes precedence.

## Rules of Precedence
When an element contains both a `ht-root-bind` and a `ht-bind` attribute, `ht-bind` will always take precedence. This is
because `ht-bind` is assumed to be more contextually specific to the element's current location within the data structure,
thus it overrides the broader `ht-root-bind` which accesses root-level data.

## Example and Explanation
Consider an element designed to display a user's name, which might exist at both the root level and within a nested data
structure:
```html
<!-- Example of attribute precedence -->
<div ht-root-bind="$.user.name" ht-bind="$.profile.name">Default Name</div>
```
In this example:

- `ht-root-bind="$.user.name"` attempts to bind the element's content to the name property of a user object at the root of the JSON data.
- `ht-bind="$.profile.name"` attempts to bind to the name property of a profile object within a locally scoped part of the JSON data.

Since `ht-bind` takes precedence over `ht-root-bind`, the content of the div will display the name from `$.profile.name`
rather than `$.user.name`.

## Use Case
This behavior is particularly useful in scenarios where a generic template is used in multiple contexts where the local
data should override the general settings defined at the root level. For instance, in a user profile editing interface,
the locally scoped name might be a field editable by the user, whereas the root-level name could represent a name
displayed in a header or menu, fetched once during initial load.

## Best Practices
- **Explicit Documentation**: Clearly document which attributes take precedence to avoid confusion for developers who might expect root-level data to take priority.
- **Avoiding Conflicts**: Whenever possible, avoid using `ht-root-bind` and `ht-bind` on the same element unless necessary, as this can lead to confusion and unexpected behaviors.
- **Clear Structure**: Maintain a clear and logical structure within your JSON data to minimize the need for overlapping bindings, ensuring that each element clearly corresponds to its data context.

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution
guidelines.
