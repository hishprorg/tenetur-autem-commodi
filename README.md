# @hishprorg/tenetur-autem-commodi <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

> Returns true if a value has the characteristics of a valid JavaScript data descriptor.

## Examples

`true` when the descriptor has valid properties with valid values.
`false` when not an object or when the object has invalid properties.

```js
var isDataDesc = require('@hishprorg/tenetur-autem-commodi');
var assert = require('assert');

assert.equal(true, isDataDesc({ value: 'foo' }));
assert.equal(true, isDataDesc({ value: function () {} }));
assert.equal(true, isDataDesc({ value: true }));

assert.equal(false, isDataDesc('a'));
assert.equal(false, isDataDesc(null));
assert.equal(false, isDataDesc([]));

assert.equal(false, isDataDesc({ value: 'foo', bar: 'baz' }));
assert.equal(false, isDataDesc({ value: 'foo', bar: 'baz' }));
assert.equal(false, isDataDesc({ value: 'foo', get: function () {} }));
assert.equal(false, isDataDesc({ get: function () {}, value: 'foo' }) );
 
assert.equal(false, isDataDesc({ value: 'foo', enumerable: 'foo' }));
assert.equal(false, isDataDesc({ value: 'foo', configurable: 'foo' }));
assert.equal(false, isDataDesc({ value: 'foo', writable: 'foo' }));
```

## Valid properties

The only valid data descriptor properties are the following:

* `configurable` (required)
* `enumerable` (required)
* `value` (optional)
* `writable` (optional)

To be a valid data descriptor, either `value` or `writable` must be defined.

**Invalid properties**

A descriptor may have additional _invalid_ properties (an error will **not** be thrown).

```js
var foo = {};

Object.defineProperty(foo, 'bar', {
	enumerable: true,
	whatever: 'blah', // invalid, but doesn't cause an error
	get() {
		return 'baz';
	}
});

assert.equal(foo.bar, 'baz');
```

### Related projects

* [is-accessor-descriptor](https://npmjs.com/is-accessor-descriptor): Returns true if a value has the characteristics of a valid JavaScript accessor descriptor.
* [is-descriptor](https://npmjs.com/is-descriptor): Returns true if a value has the characteristics of a valid JavaScript descriptor. Works for… [more](https://npmjs.com/is-descriptor)

## Tests

Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@hishprorg/tenetur-autem-commodi
[npm-version-svg]: https://versionbadg.es/inspect-js/@hishprorg/tenetur-autem-commodi.svg
[deps-svg]: https://david-dm.org/inspect-js/@hishprorg/tenetur-autem-commodi.svg
[deps-url]: https://david-dm.org/inspect-js/@hishprorg/tenetur-autem-commodi
[dev-deps-svg]: https://david-dm.org/inspect-js/@hishprorg/tenetur-autem-commodi/dev-status.svg
[dev-deps-url]: https://david-dm.org/inspect-js/@hishprorg/tenetur-autem-commodi#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hishprorg/tenetur-autem-commodi.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hishprorg/tenetur-autem-commodi.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hishprorg/tenetur-autem-commodi.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hishprorg/tenetur-autem-commodi
[codecov-image]: https://codecov.io/gh/inspect-js/@hishprorg/tenetur-autem-commodi/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/inspect-js/@hishprorg/tenetur-autem-commodi/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/inspect-js/@hishprorg/tenetur-autem-commodi
[actions-url]: https://github.com/hishprorg/tenetur-autem-commodi/actions
