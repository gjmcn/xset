# xset

Subclass of JavaScript's [built-in `Set`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) with extra methods.

## Usage:

Install:

```
install --save @gjmcn/xset
```

The module has a single named export: `XSet`.

## Methods

Use any `Set` methods as well as:

| Method | Description | Return |
|:---|:---|:---|
| `copy()` | Shallow copy. `xs.copy()` is equivalent to `new XSet(xs)`. | xset |
| `adds(iterable)` | Add each element of `iterable` to the xset. | xset |
| `deletes(iterable)` | Delete each element of `iterable` from the xset. | xset |
| `filter(f, returnArray)` | Each element is passed to the function `f`; if `f` returns a truthy value, the element is included in the result. If `returnArray` is truthy, `filter` returns a new array, otherwise returns a new xset. | xset or<br>array |
| `map(f, returnArray)` | Each element is passed to the function `f`; the returned values are collected in a new array (if `returnArray` is truthy) or a new xset. | xset or<br>array |
| `count(f)` | Each element is passed to the function `f`; `count` returns the number of times that `f` returns a truthy value. | number |
| `find(f)` | Each element is passed to the function `f`; the first time `f` returns a truthy value, the corresponding element is returned. `find` returns `undefined` if no element produces a truthy value. | any |
| `every(f)` | Each element is passed to the function `f`; if `f` returns a truthy value every time, `every` returns `true` &mdash; and returns `false` otherwise. | boolean |
| `some(f)` | Each element is passed to the function `f`; the first time `f` returns a truthy value, `some` returns `true`. If `f` returns a falsy value every time, `some` returns `false`. | boolean |
| `first()` | First element of the set, or `undefined` if the set is empty. | any |
| `difference(iterable1, iterable2, ...)` | Returns a new xset containing every element in the calling xset that is not in any of the passed iterables. | xset |
| `intersection(iterable1, iterable2, ...)` | Returns a new xset containing every element that appears in the calling xset <i>and all</i> of the passed iterables. The order of elements in the returned xset matches their order in the calling xset. | xset |
| `union(iterable1, iterable2, ...)` | Returns a new xset containing every element that appears in the calling xset or any of the passed iterables. The order of elements in the returned xset is based on their first occurrence in the calling xset and iterables. | xset |

## Example

```js
const s = new XSet([3, 4, 5]);   // XSet {3, 4, 5}
s.add(10);                       // XSet {3, 4, 5, 10}
s.adds([20, 30]);                // XSet {3, 4, 5, 10, 20, 30}

s.filter(e => e < 15);           // new Xset {3, 4, 5, 10}
s.intersection([0, 5, 10, 15]);  // new XSet {5, 10}
```