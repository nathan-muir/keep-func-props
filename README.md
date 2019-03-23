[![Codecov](https://img.shields.io/codecov/c/github/ehmicky/keep-func-props.svg?label=tested&logo=codecov)](https://codecov.io/gh/ehmicky/keep-func-props) [![Travis](https://img.shields.io/badge/cross-platform-4cc61e.svg?logo=travis)](https://travis-ci.org/ehmicky/keep-func-props) [![Node](https://img.shields.io/node/v/keep-func-props.svg?logo=node.js)](https://www.npmjs.com/package/keep-func-props) [![Gitter](https://img.shields.io/gitter/room/ehmicky/keep-func-props.svg?logo=gitter)](https://gitter.im/ehmicky/keep-func-props)

Wrap a function without changing its name, length and other properties.

Function wrappers return a new function which means the original
function's `name`, `length` and other properties are usually lost. This module
enhances them to keep those properties instead.

Function wrappers are commonly used in functional programming. They take a
function as input and return it wrapped. Examples include
[memoizing](https://github.com/planttheidea/moize) or ensuring a function is
only called once.

# Example

<!-- eslint-disable import/no-extraneous-dependencies, import/no-internal-modules, node/no-extraneous-require -->

```js
const keepFuncProps = require('keep-func-props')
// Any function wrapper works
const memoize = require('lodash/memoize')

const betterMemoize = keepFuncProps(memoize)

const anyFunction = () => true

console.log(memoize(anyFunction)) // `[Function: memoized]`
console.log(betterMemoize(anyFunction)) // `[Function: anyFunction]`
```

# Demo

You can try this library:

- either directly [in your browser](https://repl.it/@ehmicky/keep-func-props).
- or by executing the [`examples` files](examples/README.md) in a terminal.

# Install

```bash
npm install keep-func-props
```

# Usage

<!-- eslint-disable import/no-extraneous-dependencies, node/no-extraneous-require -->

```js
const keepFuncProps = require('keep-func-props')

// Any function wrapper works
const wrapper = function(anyFunction) {
  return (...args) => anyFunction(...args)
}

// `betterWrapper` is like `wrapper` but it keeps the function properties
const betterWrapper = keepFuncProps(wrapper)
```

## keepFuncProps(wrapper)

`wrapper`: `function(anyFunction, [...args]) => newFunction`<br>
_Returns_: new `wrapper`

A function wrapper is passed as argument. A copy of it is returned.

# See also

- [`mimic-fn`](https://github.com/sindresorhus/mimic-fn): same but for
  functions that do not wrap other functions.

# Contributors

<!-- ALL-CONTRIBUTORS-LIST:START -->
<!-- prettier-ignore -->
<table><tr><td align="center"><a href="https://twitter.com/ehmicky"><img src="https://avatars2.githubusercontent.com/u/8136211?v=4" width="100px;" alt="ehmicky"/><br /><sub><b>ehmicky</b></sub></a><br /><a href="https://github.com/ehmicky/keep-func-props/commits?author=ehmicky" title="Code">💻</a> <a href="#design-ehmicky" title="Design">🎨</a> <a href="#ideas-ehmicky" title="Ideas, Planning, & Feedback">🤔</a> <a href="https://github.com/ehmicky/keep-func-props/commits?author=ehmicky" title="Documentation">📖</a></td></tr></table>

<!-- ALL-CONTRIBUTORS-LIST:END -->
