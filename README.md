# ECMAScript proposal: `Promise.any`

## Status

This proposal is at stage 0 of [the TC39 process](https://tc39.github.io/process-document/).

## Motivation

There are four main combinators in the `Promise` landscape.

- `Promise.all` was added in ES2015 ✅
- `Promise.race` was added in ES2015 ✅
- [`Promise.allSettled`](https://github.com/tc39/proposal-promise-allSettled) is being proposed ✅
- `Promise.any` 🆕 (this proposal)

These are all commonly available in userland promise libraries, and they’re all independently useful, each one serving different use cases.

## Proposed solution

`Promise.any` accepts an array of promises and returns a promise that is fulfilled by the first given promise to be fulfilled, or rejected if all of the given promises are rejected.

## High-level API

```js
try {
  const first = await Promise.any(promises);
  // Any of the promises was fulfilled.
} catch (reasons) {
  // All of the promises were rejected.
}
```

Or, without `async`/`await`:

```js
Promise.any(promises).then(
  (first) => {
    // Any of the promises was fulfilled.
  },
  (reasons) => {
    // All of the promises were rejected.
    // `reasons` is an array containing the rejection reasons.
  }
);
```

### FAQ

#### Why choose the name `any`?

It clearly describes what it does, and there’s precedent for the name `any` in userland libraries offering this functionality:

- https://github.com/kriskowal/q#combination
- http://bluebirdjs.com/docs/api/promise.any.html
- https://github.com/m0ppers/promise-any
- https://github.com/cujojs/when/blob/master/docs/api.md#whenany

## Illustrative examples

TODO

## TC39 meeting notes

- TODO

## Specification

- [Ecmarkup source](https://github.com/tc39/proposal-promise-any/blob/master/spec.html)
- [HTML version](https://tc39.github.io/proposal-promise-any/)

## Implementations

- none yet
