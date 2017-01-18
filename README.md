Finnish SSN validation and creation
===================================

[![Build Status](https://travis-ci.org/vkomulai/finnish-ssn.svg?branch=master)](https://travis-ci.org/vkomulai/finnish-ssn) ![0 deps](https://david-dm.org/vkomulai/finnish-ssn.svg) ![Downloads](https://img.shields.io/npm/dt/finnish-ssn.svg) ![License](https://img.shields.io/npm/l/finnish-ssn.svg)


- A micro Javascript library for validating and creating Finnish social security numbers
- Lightweight, 3.5kB (1.5kB gzipped)
- No dependencies

Installation
------------

NPM

```sh
npm install finnish-ssn
```

Bower

```sh
bower install finnish-ssn
```

From unpkg.com

```html
<script src="https://unpkg.com/finnish-ssn/dist/finnish-ssn.min.js"></script>
```


Usage
-----

ES6

``` js
import FinnishSSN from "../finnish-ssn"
const isValid = FinnishSSN.validate('010101-100X');
console.log(isValid);
//  Yields true

```

Oldskool Web: Writes FinnishSSN into global namespace.

``` html
<script src="https://unpkg.com/finnish-ssn/finnish-ssn.min.js"></script>
<script>
  // This is valid SSN
  var isValid = FinnishSSN.validate('290296-7808');
  console.log(isValid);
  //  Yields true
</script>

```

Examples
--------

Validate an SSN

``` js
//  This is valid SSN
console.log('valid ssn returns ' + FinnishSSN.validate('290296-7808'));
//  'valid ssn returns true'

//  This is invalid SSN
console.log('invalid ssn returns ' + FinnishSSN.validate('010198-1000'));
//  'invalid ssn returns false'

```
Parse SSN

``` js
//  This is valid SSN
var parsedSsn =  FinnishSSN.parse('290296-7808');
//  This is invalid SSN
console.log(parsedSsn);
{
  valid: true,
  sex: 'female',
  ageInYears: 19,
  dateOfBirth: Thu Feb 29 1996 00:00:00 GMT+0200 (EET)
}
```

Create an SSN for person that is 20 years old.

``` js
console.log('SSN for person that is 20 years old ' + FinnishSSN.createWithAge(20));
//  SSN for person that is 20 years old 010195-XXXX
```

Functions
---------

### #validate(ssn)

- Validates parameter given SSN. Returns true if SSN is valid, otherwise false

### #parse(ssn)

- Parses parameter given SSN. Returns object ``{valid: boolean, sex: "male|female", ageInYears: Number, dateOfBirth: Date }``

```js
{
  valid: false,
  sex: null,
  ageInYears: null,
  dateOfBirth: null
}
{
  valid: true,
  sex: 'male',
  ageInYears: 15,
  dateOfBirth: Tue Feb 29 2000 00:00:00 GMT+0200 (EET)
}
{
  valid: true,
  sex: 'female',
  ageInYears: 15,
  dateOfBirth: Mon Feb 28 2000 00:00:00 GMT+0200 (EET)
}
```

### #createWithAge(age)

- Creates a valid SSN using the given age (Integer). Generates randomly male and female SSN'n.

Building
--------

```sh
# Build a distributable, minified UMD library compatible with browsers and Node
npm run dist

# Run tests
npm run test

# Run tests in watch-mode
npm run test:watch
```

Changelog
---------
### 1.1.1
- FIXED: [Issue 6: Bug in calculating age](https://github.com/vkomulai/finnish-ssn/issues/6)

### 1.1.0
- Sources ported from ES5 --> ES6
- Distributed js is transpiled to ES5 for backwards compatibility
- API should still be backwards compatible with `1.0.3`. Bumping minor-version to be on the safe side.

### 1.0.3
- FIXED: [Issue 2: Replace npmcdn.com with unpkg.com](https://github.com/vkomulai/finnish-ssn/issues/2)

### 1.0.2
- FIXED: [Issue 1: Length is not verified](https://github.com/vkomulai/finnish-ssn/issues/1)

### 1.0.1
- Clean semicolons, removed lodash

### 1.0.0
- Initial release

Future development
------------------
- FlowType
- Use a better js doc tool

License
-------

[MIT License](LICENSE)
