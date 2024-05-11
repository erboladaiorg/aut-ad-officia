# @erboladaiorg/aut-ad-officia <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.toSpliced` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-change-array-by-copy/#sec-array.prototype.toSpliced).

Because `Array.prototype.toSpliced` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @erboladaiorg/aut-ad-officia
```

## Usage/Examples

```js
var toSpliced = require('@erboladaiorg/aut-ad-officia');
var assert = require('assert');

var input = [5, 4, 3, 2, 1, 0];

var output = toSpliced(input, 2, 2);

assert.notEqual(output, input);
assert.deepEqual(output, [5, 4, 1, 0]);
assert.deepEqual(input, [5, 4, 3, 2, 1, 0]);
```

```js
var toSpliced = require('@erboladaiorg/aut-ad-officia');
var assert = require('assert');
/* when Array#toSpliced is not present */
delete Array.prototype.toSpliced;
var shimmed = toSpliced.shim();

assert.equal(shimmed, toSpliced.getPolyfill());
assert.deepEqual(input.toSpliced(), toSpliced(input));
```

```js
var toSpliced = require('@erboladaiorg/aut-ad-officia');
var assert = require('assert');
/* when Array#toSpliced is present */
var shimmed = toSpliced.shim();

assert.equal(shimmed, Array.prototype.toSpliced);
assert.deepEqual(input.toSpliced(), toSpliced(input));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@erboladaiorg/aut-ad-officia
[npm-version-svg]: https://versionbadg.es/erboladaiorg/aut-ad-officia.svg
[deps-svg]: https://david-dm.org/erboladaiorg/aut-ad-officia.svg
[deps-url]: https://david-dm.org/erboladaiorg/aut-ad-officia
[dev-deps-svg]: https://david-dm.org/erboladaiorg/aut-ad-officia/dev-status.svg
[dev-deps-url]: https://david-dm.org/erboladaiorg/aut-ad-officia#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@erboladaiorg/aut-ad-officia.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@erboladaiorg/aut-ad-officia.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@erboladaiorg/aut-ad-officia.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@erboladaiorg/aut-ad-officia
