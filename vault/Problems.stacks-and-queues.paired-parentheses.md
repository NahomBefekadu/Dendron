---
id: RrG5ujLHBbCFiqM3qCxVI
title: paired-parentheses
desc: ""
updated: 1644419186728
created: 1644418841042
---

## Question

given a string of characters return a boolean indicating whether or not the string has well-formed parentheses.

#### input:

(david)((abby))

#### Output:

TRUE

## Solution

The way we can solve is using a counter, where we can increment a counter if we find an opening parentheses and decrement if we encounter a closing parentheses.

#### Javascript

```javascript
const pairedParentheses = (str) => {
  let count = 0;
  for (const char of str) {
    if (char === "(") {
      count++;
    } else if (char === ")") {
      if (count === 0) return false;
      count--;
    }
  }
  return count === 0;
};
```

#### Java

```java

```

## Concepts
