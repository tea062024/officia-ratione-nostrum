# @tea062024/officia-ratione-nostrum <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2019 spec-compliant `Array.prototype.flat` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.github.io/proposal-flatMap/).

Because `Array.prototype.flat` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @tea062024/officia-ratione-nostrum
```

## Usage/Examples

```js
var flat = require('@tea062024/officia-ratione-nostrum');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];

assert.deepEqual(flat(arr, 1), [1, 2, 3, [4]]);
```

```js
var flat = require('@tea062024/officia-ratione-nostrum');
var assert = require('assert');
/* when Array#flat is not present */
delete Array.prototype.flat;
var shimmedFlat = flat.shim();

assert.equal(shimmedFlat, flat.getPolyfill());
assert.deepEqual(arr.flat(), flat(arr));
```

```js
var flat = require('@tea062024/officia-ratione-nostrum');
var assert = require('assert');
/* when Array#flat is present */
var shimmedIncludes = flat.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, Array.prototype.flat);
assert.deepEqual(arr.flat(mapper), flat(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@tea062024/officia-ratione-nostrum
[npm-version-svg]: https://versionbadg.es/tea062024/officia-ratione-nostrum.svg
[deps-svg]: https://david-dm.org/tea062024/officia-ratione-nostrum.svg
[deps-url]: https://david-dm.org/tea062024/officia-ratione-nostrum
[dev-deps-svg]: https://david-dm.org/tea062024/officia-ratione-nostrum/dev-status.svg
[dev-deps-url]: https://david-dm.org/tea062024/officia-ratione-nostrum#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@tea062024/officia-ratione-nostrum.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@tea062024/officia-ratione-nostrum.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@tea062024/officia-ratione-nostrum.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@tea062024/officia-ratione-nostrum
[codecov-image]: https://codecov.io/gh/tea062024/officia-ratione-nostrum/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/tea062024/officia-ratione-nostrum/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/tea062024/officia-ratione-nostrum
[actions-url]: https://github.com/tea062024/officia-ratione-nostrum/actions
