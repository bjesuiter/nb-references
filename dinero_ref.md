---
title: "Dinero.js v2 - JavaScript money handling library"
anchor: Reliable money/currency handling in JS - avoids floating-point precision issues, tree-shakeable functions
tags: [javascript, money, currency, library, floating-point]
description: JavaScript library for creating, calculating, and formatting money - represents money as integers in minor units
source_url: https://www.sarahdayan.com/blog/dinerojs-v2-is-out
---

## Reference

### Summary
JavaScript library for handling money without floating-point precision issues. v2 is a full rewrite with tree-shakeable functions and proper currency metadata.

### Key Features
- **No floating-point errors:** Money stored as integers (cents/pence)
- **Tree-shakeable:** Import only what you need (vs v1's chainable prototype methods)
- **166 ISO 4217 currencies** with correct metadata (code, base, exponent)
- **Functional style:** Functions compose well with utilities like Ramda

### Example
```js
import { dinero, add, toDecimal } from 'dinero.js';
import { USD } from 'dinero.js/currencies';

const price = dinero({ amount: 500, currency: USD }); // $5.00
const fee = dinero({ amount: 100, currency: USD });   // $1.00

toDecimal(add(price, fee)); // "6.00"
```

### Links
- https://www.dinerojs.com/
- https://github.com/dinerojs/dinero.js
