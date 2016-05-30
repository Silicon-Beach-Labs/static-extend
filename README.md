# static-extend [![NPM version](https://img.shields.io/npm/v/static-extend.svg?style=flat)](https://www.npmjs.com/package/static-extend) [![NPM downloads](https://img.shields.io/npm/dm/static-extend.svg?style=flat)](https://npmjs.org/package/static-extend) [![Build Status](https://img.shields.io/travis/jonschlinkert/static-extend.svg?style=flat)](https://travis-ci.org/jonschlinkert/static-extend)

Adds a static `extend` method to a class, to simplify inheritance. Extends the static properties, prototype properties, and descriptors from a `Parent` constructor onto `Child` constructors.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install static-extend --save
```

## Usage

```js
var extend = require('static-extend');
```

## API

### [extend](index.js#L46)

Returns a function for extending the static properties, prototype properties, and descriptors from the `Parent` constructor onto `Child` constructors.

**Params**

* `Parent` **{Function}**: Parent ctor
* `extendFn` **{Function}**: Optional extend function for handling any necessary custom merging. Useful when updating methods that require a specific prototype.
* `Child` **{Function}**: Child ctor
* `proto` **{Object}**: Optionally pass additional prototype properties to inherit.
* `returns` **{Object}**

**Example**

```js
var extend = require('static-extend');
Parent.extend = extend(Parent);

// optionally pass a custom merge function as the second arg
Parent.extend = extend(Parent, function(Child) {
  Child.prototype.mixin = function(key, val) {
    Child.prototype[key] = val;
  };
});

// extend "child" constructors
Parent.extend(Child);

// optionally define prototype methods as the second arg
Parent.extend(Child, {
  foo: function() {},
  bar: function() {}
});
```

## Contributing

This document was generated by [verb](https://github.com/verbose/verb), please don't edit directly. Any changes to the readme must be made in [.verb.md](.verb.md). See [Building Docs](#building-docs).

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/static-extend/issues/new).

## Building docs

Generate readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install -g verb verb-readme-generator && verb
```

## Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

## Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/jonschlinkert/static-extend/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on May 29, 2016._