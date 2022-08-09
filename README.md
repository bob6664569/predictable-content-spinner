# content-spinner

[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

Node.js recursive content spinner algorithm with available predictable behavior. 

Based on [string-content-spinner](https://github.com/heek/string-content-spinner) ([@heek](https://github.com/heek/))

## API

### The `spin` function

Spin a string.

Parameters:

```js
spin(stringToSpin: string[, seed: string]);
```

### Example without seed parameter:

```js
const spin = require('content-spinner');

const result = spin('{Hello|Good morning} world');

console.log(result);
```
This will log either `Hello world` or `Good morning world`.

### Example with a seed parameter:

```js
const spin = require('predictable-content-spinner');

const result = spin('{Hello|Good morning} world', 'Random text');

console.log(result);
```
This example will always product the same output with the same string passed as the second parameter.

### The `factory` function

Generates a new `spin` function with custom section markers and delimiter.

Parameters:

```js
factory(openSectionMarker: string, closeSectionMarker: string, delimiter: string);
```

Example:

```js
// Get factory function
const spinFactory = require('string-content-spinner').factory;

// Generate new spin function with custom section markers and delimiter
const spin = spinFactory('[[', ']]', '::');

// Use it!
const result = spin('Hello [[world::mars]]');

console.log(result);
```

This will log either `Hello world` or `Hello mars`.

## Development

### NPM commands

- `npm run prettier`: run prettier on source files (both lib and test files)
- `npm run lint`: lint source files (both lib and test files, using `eslint`)
- `npm test` or `npm run test`: run unit tests
- `npm run git-add`: run prettor, lint and unit tests, if all passed, stage changes


