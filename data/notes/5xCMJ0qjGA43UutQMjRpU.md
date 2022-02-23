
## Question

Given a string, find the length of the longest substring in it with no more than K distinct characters.

#### input:

Input: String="araaci", K=2

#### Output:

Output: 4
"araa"

## Solution

We can approach this problem by using our SlidingWindow pattern. We will be using a map to keep track of the unique characters in our string and increment our char each time we come to a new character. As we do this we want to check if our length of our object is greater than k. If it is we have to resize our window using our windowStart index until the length of our object is less than k.

As we do this we are tracking the length our max object, to return.

#### Javascript

```javascript
const longest_substring_with_k_distinct = function (str, k) {
  let windowStart = 0;
  const mem = {};
  let result = 0;
  for (windowEnd = 0; windowEnd < str.length; windowEnd++) {
    if (!(str[windowEnd] in mem)) {
      mem[str[windowEnd]] = 0;
    }
    mem[str[windowEnd]] += 1;
    while (Object.keys(mem).length > k) {
      mem[str[windowStart]] -= 1;
      if (mem[str[windowStart]] === 0) {
        delete mem[str[windowStart]];
      }
      windowStart++;
    }
    result = Math.max(result, windowEnd - windowStart + 1);
  }
  return result;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- sliding window
- Map/Set
