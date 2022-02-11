---
id: uLbeeEPOK6aYy7t8qQYFB
title: balanced-brackets
desc: ""
updated: 1644420911738
created: 1644419279996
---

## Question

Given a string as input return a boolean indicating whether the string contains matching brackets

#### input:

input = "(){}[](<()>)"

#### Output:

true

## Solution

#### Javascript

```javascript
const stack = [];
const brackets = {
  "(": ")",
  "{": "}",
  "[": "]",
};
const closingBracket = "}])";

for (const char of string) {
  if (char in brackets) {
    stack.push(brackets[char]);
  } else if (closingBracket.includes(char)) {
    if (stack[stack.length - 1] === char && stack.length > 0) {
      stack.pop();
    } else {
      return false;
    }
  } else {
    continue;
  }
}
return stack.length === 0;
```

#### Java

```java

```

## Concepts
