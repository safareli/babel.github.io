---
layout: docs
title: ES5 property mutators transform
description:
permalink: /docs/plugins/transform-es5-property-mutators/
---

Turn [object initializer mutators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#Method_definitions) into `Object.defineProperties`.

## Example

**In**

```javascript
var foo = {
  get bar() {
    return "bar";
  }
};
```

**Out**

```javascript
var foo = Object.defineProperties({}, {
  bar: {
    get: function () {
      return "bar";
    },
    enumerable: true,
    configurable: true
  }
});

## Installation

```sh
$ npm install babel-plugin-transform-es5-property-mutators
```

## Usage

Add the following line to your `.babelrc` file:

```json
{
  "plugins": ["transform-es5-property-mutators"]
}
```
