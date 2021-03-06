---
layout: docs
title: React constant elements transformer
description:
permalink: /docs/plugins/transform-react-constant-elements/
---

Hoists element creation to the top level for subtrees that are fully static, which reduces call to `React.createElement` and the resulting allocations. More importantly, it tells React that the subtree hasn't changed so React can completely skip it when reconciling.

This transform **should be enabled only in production** (e.g., just before minifying your code) because although they improve runtime performance, they make warning messages more cryptic and skip important checks that happen in development mode, including propTypes.

**In**

```javascript
class MyComponent extends React.Component {
  render() {
    return <ul>
      <li>This</li>
      <li>is</li>
      <li>completely</li>
      <li>static</li>
    </ul>;
  }
}
```

**Out**

```javascript
var _hoistedElement = React.createElement(
    "ul",
    null,
    React.createElement(
      "li",
      null,
      "This"
    ),
    React.createElement(
      "li",
      null,
      "is"
    ),
    React.createElement(
      "li",
      null,
      "completely"
    ),
    React.createElement(
      "li",
      null,
      "static"
    )
  );
});

class MyComponent extends React.Component {
  render() {
    return _hoistedElement;
  }
}
```

## Installation

```sh
$ npm install babel-plugin-transform-react-constant-elements
```

## Usage

Add the following line to your `.babelrc`:

```json
{
  "plugins": ["transform-react-constant-elements"]
}
``
