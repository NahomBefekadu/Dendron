---
id: cs1rep96HogEwddBbZ1al
title: decompress
desc: ""
updated: 1644896219958
created: 1644425729526
---

## Question

given a compressed string as input, return a string that is decompressed.

#### input:

("2{q}3{tu}v")
("2{y3{o}}v")

#### Output:

qqtututuv
yoooyooos

## Solution

as seen from our input we can have nested compressed strings so we have to evaluate our strings carefully.

if we don't have any nesteed groups we could use a stack to remember the different gro

#### Javascript

```javascript
const decompressBraces = (s) => {
  const stack = [];
  const numbers = "123456789";

  for (const char of s) {
    //console.log(stack)
    if (numbers.includes(char)) {
      stack.push(Number(char));
    } else {
      if (char === "}") {
        //pop routine
        let str = "";
        while (typeof stack[stack.length - 1] !== "number") {
          let popped = stack.pop();
          str = popped + str;
        }
        let num = stack.pop();
        let finStr = str.repeat(num);
        console.log(finStr);
        stack.push(finStr);
      } else if (char !== "{") {
        stack.push(char);
      }
    }
  }
  console.log(stack);
  return stack.join("");
};
```

#### Java

```java

```

## Concepts

[[data-structures.stacks]]

## Patterns

- Stack
