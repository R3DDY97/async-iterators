# async-iterators
Asynchronous iterators for event handilng in JavaScript

## install
Just copy __index.mjs__ to the relevant folder or

```bash

$ npm install @santoshrajan/async-iterators
```

## Example

```html

<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Click Counter</title>
  </head>
<body>
  <h1>Click Counter</h1>
  <div id='counter'></div>
  <button id='plus'>+</button>
  <button id='minus'>-</button>

<script type='module'>

import {
  clickIterator,
  mapIterator,
  mergeIterators,
  runIterator
 } from './index.mjs'

const store = function createStore () {
  var counter = 0
  return (n) => counter += n
}()

function render (n) {
  document.querySelector('#counter').textContent = n
  return n
}

let plusIterator = clickIterator('#plus')
plusIterator = mapIterator(plusIterator, e => store(1))

let minusIterator = clickIterator('#minus')
minusIterator = mapIterator(minusIterator, e => store(-1))

const allIterator = mergeIterators(plusIterator, minusIterator)

runIterator(allIterator, render)

render(0)

</script>
</body>
</html>
```
