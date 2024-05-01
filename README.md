# @devtea2026/nisi-officiis-et-fuga <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.at` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://github.com/tc39/proposal-relative-indexing-method).

Because `Array.prototype.at` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @devtea2026/nisi-officiis-et-fuga
```

## Usage/Examples

```js
var at = require('@devtea2026/nisi-officiis-et-fuga');
var assert = require('assert');

var arr = [1, [2], [], 3];

var results = at(arr, function (x, i) {
	assert.equal(x, arr[i]);
	return x;
});

assert.deepEqual(results, [1, 2, 3]);
```

```js
var at = require('@devtea2026/nisi-officiis-et-fuga');
var assert = require('assert');
/* when Array#at is not present */
delete Array.prototype.at;
var shimmedFlatMap = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedFlatMap, at.getPolyfill());
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

```js
var at = require('@devtea2026/nisi-officiis-et-fuga');
var assert = require('assert');
/* when Array#at is present */
var shimmedIncludes = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, Array.prototype.at);
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@devtea2026/nisi-officiis-et-fuga
[npm-version-svg]: https://versionbadg.es/devtea2026/nisi-officiis-et-fuga.svg
[deps-svg]: https://david-dm.org/devtea2026/nisi-officiis-et-fuga.svg
[deps-url]: https://david-dm.org/devtea2026/nisi-officiis-et-fuga
[dev-deps-svg]: https://david-dm.org/devtea2026/nisi-officiis-et-fuga/dev-status.svg
[dev-deps-url]: https://david-dm.org/devtea2026/nisi-officiis-et-fuga#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@devtea2026/nisi-officiis-et-fuga.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@devtea2026/nisi-officiis-et-fuga.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@devtea2026/nisi-officiis-et-fuga.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@devtea2026/nisi-officiis-et-fuga
[codecov-image]: https://codecov.io/gh/devtea2026/nisi-officiis-et-fuga/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/devtea2026/nisi-officiis-et-fuga/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/devtea2026/nisi-officiis-et-fuga
[actions-url]: https://github.com/devtea2026/nisi-officiis-et-fuga/actions
