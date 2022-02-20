---
id: xw9U0jQ4XyOZiDvijvqbg
title: uncompress-string
desc: ""
updated: 1644941355530
created: 1644514783771
---

## Question

Given a String as an input, uncompress each character and repeat it based on the number indicated.

#### input:

uncompress("2c3a1t")

#### Output:

'ccaaat'

## Solution

We can solve this by iterating over our string input. First we can have an array of possible numbers in the string to check each character against.

We will then have to pointers to loop through the array. for our first pointer, as we loop we check to see that the character currently is in our number array. If it's in our number array we simply increment our first pointer.

Once we reach a character which is not in our number array we take a slice from our second pointer which is at the start to our first pointer. This will give us the number we need to repeat our given character.

Now we take our given character and use a simple for loop or repeat function to push our repeated character into our results array. After we have pushed our array we then simply equal our second pointer to our first pointer, and increment our first pointer. We then go through this loop until we have reached the end of our string.

#### Javascript

```javascript
const uncompress = (s) => {
  let result = [];
  const numbers = "0123456789";
  let i = 0;
  let j = 0;
  while (j < s.length) {
    if (numbers.includes(s[j])) {
      j += 1;
    } else {
      const num = Number(s.slice(i, j));
      for (let count = 0; count < num; count += 1) {
        result.push(s[j]);
      }
      j += 1;
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

[[data-structures.arrays]]

## Patterns

- Two Pointers
- One Fast one Slow pointer
