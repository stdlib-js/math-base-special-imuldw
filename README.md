<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# imuldw

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] [![dependencies][dependencies-image]][dependencies-url]

> Compute the double word product of two signed 32-bit integers.

<section class="intro">

</section>

<!-- /.intro -->

<section class="installation">

## Installation

```bash
npm install @stdlib/math-base-special-imuldw
```

</section>

<section class="usage">

## Usage

```javascript
var imuldw = require( '@stdlib/math-base-special-imuldw' );
```

#### imuldw( \[out,] a, b )

Multiplies two signed 32-bit integers and returns an `array` of two signed 32-bit integers which represents the signed 64-bit integer product.

```javascript
var v = imuldw( 1, 10 );
// returns [ 0, 10 ]

v = imuldw( 0x80000000|0, 0x40000000|0 ); // -(2^31) * 2^30 = -2305843009213694000 => 32-bit integer overflow
// returns [ -536870912, 0 ]
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   When computing the product of 32-bit integer values in double-precision floating-point format (the default JavaScript numeric data type), computing the double word product is necessary in order to **avoid** exceeding the [maximum safe double-precision floating-point integer value][@stdlib/constants/float64/max-safe-integer].

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var lpad = require( '@stdlib/string-left-pad' );
var imuldw = require( '@stdlib/math-base-special-imuldw' );

var i;
var j;
var y;

for ( i = 0x7FFFFFF0; i < 0x7FFFFFFF; i++ ) {
    for ( j = i; j < 0x7FFFFFFF; j++) {
        y = imuldw( i|0, j|0 );
        console.log( '%d x %d = 0x%s%s', i|0, j|0, lpad( ( y[0] >>> 0 ).toString( 16 ), 8, '0'), lpad( ( y[1] >>> 0 ).toString( 16 ), 8, '0' ) );
    }
}
```

</section>

<!-- /.examples -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2021. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/math-base-special-imuldw.svg
[npm-url]: https://npmjs.org/package/@stdlib/math-base-special-imuldw

[test-image]: https://github.com/stdlib-js/math-base-special-imuldw/actions/workflows/test.yml/badge.svg
[test-url]: https://github.com/stdlib-js/math-base-special-imuldw/actions/workflows/test.yml

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/math-base-special-imuldw/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/math-base-special-imuldw?branch=main

[dependencies-image]: https://img.shields.io/david/stdlib-js/math-base-special-imuldw.svg
[dependencies-url]: https://david-dm.org/stdlib-js/math-base-special-imuldw/main

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/math-base-special-imuldw/main/LICENSE

[@stdlib/constants/float64/max-safe-integer]: https://github.com/stdlib-js/constants-float64-max-safe-integer

</section>

<!-- /.links -->
