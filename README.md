# HTMT
HyperText Markup Templating

WARNING! Working Draft Alpha!

## Description
HTMT is a client-side and server-side templating engine designed to seamlessly integrate with 
HTML/[HTMX](https://htmx.org/), using *[JSONPath](https://www.ietf.org/archive/id/draft-goessner-dispatch-jsonpath-00.html)* 
for dynamic data binding and manipulation. It extends standard HTML with custom data attributes, enabling powerful, 
declarative rendering and state management directly in the markup.

## Documentation
For the full documentation go to: [`./docs` directory](./docs).

## Features
HTMT uses a series of custom `ht-*` attributes to bind data, control element visibility, iterate over collections, and 
dynamically apply CSS classes based on the state of the data. Below is a table of the available attributes, their 
descriptions, and examples:

| Attribute                                     | Description                                                                               | Example                                                          |
|-----------------------------------------------|-------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| [`ht-bind`](./docs/ht-bind.md)                | Binds data to the element's content or specific attributes.                               | `<div ht-bind="$.user.name"></div>`                              |
| [`ht-loop`](./docs/ht-loop.md)                | Iterates over an array or collection, rendering the enclosed block for each item.         | `<div ht-loop="$.users[*]"><span ht-bind="$.name"></span></div>` |
| [`ht-template`](./docs/ht-template.md)        | Specifies a template block that can be reused and instantiated within `ht-loop`.          | `<template id="user-template">...</template>`                    |
| [`ht-attr-[name]`](./docs/ht-attr.md)         | Binds data to an element's attribute.                                                     | `<img ht-attr-src="$.user.avatarUrl">`                           |
| [`ht-show`](./docs/ht-show.md)                | Shows the element if the condition is true.                                               | `<div ht-show="$.user.isLoggedIn"></div>`                        |
| [`ht-hide`](./docs/ht-hide.md)                | Hides the element if the condition is true.                                               | `<div ht-hide="$.user.isAnonymous"></div>`                       |
| [`ht-switch`](./docs/ht-switch.md)            | Evaluates an expression and renders the case block that matches the result.               | `<div ht-switch="$.user.role">...</div>`                         |
| [`ht-case`](./docs/ht-case.md)                | Specifies a case within a `ht-switch` block.                                              | `<div ht-case="'admin'">Admin content</div>`                     |
| [`ht-class-[class name]`](./docs/ht-class.md) | Applies a CSS class to the element if the condition is true.                              | `<div ht-class-active="$.user.status == 'active'"></div>`        |

## Resources for *JSONPath*
- [About | JSONPath | data tracker | IETF](https://datatracker.ietf.org/wg/jsonpath/about/)
- [JSONPath -- XPath for JSON](https://www.ietf.org/archive/id/draft-goessner-dispatch-jsonpath-00.html)
- [JSONPath Syntax | SmartBear](https://support.smartbear.com/alertsite/docs/monitors/api/endpoint/jsonpath.html)
- [JSONPath Online Evaluator](https://jsonpath.com/)

## JSONPath Libraries by Language

JSONPath is a query language for JSON, similar to XPath for XML. It is used to extract and manipulate data within JSON 
documents. Below is a list of JSONPath libraries available for various programming languages, helping developers 
integrate JSONPath functionality into their applications.

| Language   | Libraries                                                                                                                                                                                                                                               |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Java       | - [JsonPath](https://github.com/json-path/JsonPath)                                                                                                                                                                                                     |
| PHP        | - [JsonPath-PHP](https://github.com/Galbar/JsonPath-PHP)<br/>- [PECL jsonpath](https://pecl.php.net/package/jsonpath)                                                                                                                                   |
| JavaScript | - [jsonpath-plus](https://www.npmjs.com/package/jsonpath-plus)                                                                                                                                                                                          |
| Go         | - [jsonpath](https://github.com/PaesslerAG/jsonpath)<br/>- [yalp/jsonpath](https://github.com/yalp/jsonpath)                                                                                                                                            |
| Python     | - [jsonpath](https://pypi.org/project/jsonpath/)<br/>- [jsonpath-rw](https://pypi.org/project/jsonpath-rw/)<br/>- [jsonpath-rw-ext](https://pypi.org/project/jsonpath-rw-ext/)<br/>- [jsonpath-ng](https://pypi.org/project/jsonpath-ng/) (recommended) |
| Rust       | - [jsonpath-rust](https://crates.io/crates/jsonpath-rust)                                                                                                                                                                                               |
| Kotlin     | - [JsonPathKt](https://github.com/codeniko/JsonPathKt)<br/>- [kotlinx-serialization-jsonpath](https://github.com/nomisRev/kotlinx-serialization-jsonpath)                                                                                               |
| Swift      | - [SwiftPath](https://github.com/g-mark/SwiftPath)<br/>- [Sextant](https://github.com/KittyMac/Sextant)                                                                                                                                                 |
| Bash       | - [JSONPath.sh](https://github.com/bashtools/JSONPath.sh)                                                                                                                                                                                               |
| C#         | - [JSONPath](https://github.com/atifaziz/JSONPath)<br/>- [Newtonsoft JSON](https://www.newtonsoft.com/json)                                                                                                                                             |
| C++        | - [nlohmann/json](https://github.com/nlohmann/json)<br/>- [jsoncons](https://github.com/danielaparker/jsoncons)                                                                                                                                         |

> Note: The libraries listed vary in their support of the JSONPath standards. Differences in support can affect the 
> compatibility and functionality of JSONPath expressions across different projects and applications. It is recommended 
> to review the specific features and limitations of each library to ensure it meets the requirements of your use case.

## License
This document is part of the HTMT project, which is open source and freely available under the MIT License. For full
details, see the [LICENSE](./LICENSE) file and the [main README](./README.md) for project details and contribution
guidelines.
