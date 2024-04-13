# `ht-attr`
The `ht-attr` attribute in the HTMT (HyperText Markup Templating) system is designed to dynamically bind JSON data to 
the attributes of HTML elements. This powerful feature allows developers to update element attributes directly based on 
the data from their model.

## Syntax
To use `ht-attr`, specify the attribute you want to bind to and provide a JSONPath expression that evaluates to the value 
you want to set. The syntax looks like this: 
```html
<element ht-attr-[attribute-name]="expression"></element>
```
- `attribute-name`: The name of the HTML attribute you want to dynamically bind to (e.g., `src`, `href`, `class`).
- `expression`: A JSONPath expression that specifies the data from your JSON model to bind to the attribute.

## Examples
### Binding an Image Source
Dynamically setting the source of an image based on user data: 
```html
<img ht-attr-src="$.user.profilePictureUrl" alt="User Profile Picture">
```

In this example, the `src` attribute of the `<img>` tag is dynamically set to the URL provided by `$.user.profilePictureUrl` 
in the JSON model.

### Binding a Hyperlink
Setting the URL and the title of a hyperlink dynamically: 

```html
<a ht-attr-href="$.user.website" ht-attr-title="$.user.websiteTitle">Visit My Website</a>
```

This binds the `href` and `title` attributes of an `<a>` tag to properties specified in the user's data.

## Best Practices
- **Data Integrity**: Ensure that the data used for attribute bindings is sanitized and safe, particularly when binding data that could potentially include user input.
- **Efficiency**: Consider the implications of binding data to frequently changing attributes and the impact on performance, especially for attributes that cause significant changes to the document layout or appearance.
- **Fallbacks**: Provide default values or fallbacks for critical attributes in case the data binding expression evaluates to null or undefined.

## Compatibility
`ht-attr` is implemented through JavaScript and relies on JSONPath expressions for data binding. It is compatible with all 
modern browsers that support ECMAScript 2015 (ES6) and later. Make sure that your implementation handles browser-specific 
quirks, especially related to attribute behaviors (such as boolean attributes in HTML5).

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full 
details, see the [LICENSE](../LICENSE) file and the [main README](../README.md) for project details and contribution 
guidelines.
