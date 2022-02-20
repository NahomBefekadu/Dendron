---
id: zBUH1tu6FX4CsG5fa5uSB
title: compress
desc: ""
updated: 1644941473862
created: 1644941390406
---

## Question

Given a string as an input compress it to each character and the number of times they occur in the string.

#### input:

compress('ccaaatsss');

#### Output:

'2c3at3s'

## Solution

This question is really similar to our previous question of uncompressing our string.

#### Javascript

```javascript
const compress = (s) => {
  let result = [];
  let i = 0;
  let j = 0;

  while (j <= s.length) {
    if (s[i] === s[j]) {
      j += 1;
    } else {
      const num = j - i;
      if (num === 1) {
        result.push(s[i]);
      } else {
        result.push(String(num), s[i]);
      }
      i = j;
    }
  }

  return result.join("");
};
```

#### Java

```java

```

## Concepts

## Patterns
