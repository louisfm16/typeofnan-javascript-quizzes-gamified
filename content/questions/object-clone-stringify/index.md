---
title: Object Cloning (JSON.parse + JSON.stringify) Comparison
tags:
  - object
  - cloning
order: 28
date: '2019-10-05'
answers:
  - 'true true true true'
  - 'true true true false'
  - 'true true false true // correct'
  - 'false false false false'

allocatedTime: 30
---

Consider objects `a` and `b` below. What gets logged?

```javascript
const a = { 
  stringField: 'Joe',
  numberField: 123,
  dateField: new Date('1995-12-17T03:24:00'),
  nestedField: {field: 'Nested'}
};
const b = JSON.parse(JSON.stringify(a));
console.log(
  a.stringField === b.stringField,
  a.numberField === b.numberField,
  a.dateField === b.dateField,
  a.nestedField.field === b.nestedField.field
);
```

<!-- explanation -->

Setting `b = JSON.parse(JSON.stringify(a))` will perform a deep copy of object `a`. All primitive Javascript types (Boolean, String, and Number) will be copied correctly. However, non-valid JSON values (Date, undefined, Function, and other non-primitives) will not be copied correctly. In this instance, `JSON.stringify` will convert the Date object into an ISO string and it will remain a string when the stringified JSON is re-parsed. Since the two fields are different data types (Date object vs. string), the equality will yield false. See [MDN Description](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#Description) for a more detailed explanation.
