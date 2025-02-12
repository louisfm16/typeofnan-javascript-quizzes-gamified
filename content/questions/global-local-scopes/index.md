---
title: Global Local
tags:
  - variables
  - scope
  - hoisting
order: 37
date: '2019-10-06'
answers:
  - 5 and 10
  - undefined and 10 // correct
  - 5 and undefined
  - undefined and undefined
allocatedTime: 30
---

Consider the following code block. What gets logged?

```javascript
var x = 5;

(function() {
  console.log(x);
  var x = 10;
  console.log(x);
})();
```

<!-- explanation -->

This will print out `undefined` and `10`. JavaScript will hoist the `var x` declaration within the function scope, but it will not hoist the initialization. The code is equivalent to:

```javascript
var x = 5;

(function() {
  var x;
  console.log(x);
  x = 10;
  console.log(x);
})();
```
