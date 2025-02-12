---
title: Two Many Dots?
tags:
  - numbers
  - properties
order: 44
date: '2019-10-08'
answers: 
  - '[1, 2, 3, 4, 5]'
  - 'undefined // correct'
  - 'Syntax error'
allocatedTime: 30
---

What is the return of the following `console.log`?

```javascript
const n = 5;

console.log(1..n); // ?
```

<!-- explanation -->

This is not a syntax error. Rather, to call a method directly on a `Number.prototype`, two dots are required for it to not be interpreted as a decimal. In this case, `1..n` tries to access the property `n` on `1`, which is `undefined`. A practical example of this would be `1..toString()`, which would result in the string `"1"`.

To see more info on this notation, refer to: [Two dots to call a method](https://javascript.info/number#tostring-base).
