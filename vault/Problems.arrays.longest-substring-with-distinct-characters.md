---
id: XhU0p46JCUp90VJiwuQab
title: longest-substring-with-distinct-characters
desc: ""
updated: 1645159090437
created: 1645158710479
---

## Question

Given a string s, find the length of the longest substring without repeating characters.

#### input:

Input: String="aabccbb"

#### Output:

Output: 3

## Solution

As done in most of the other questions we can solve this using our sliding window and a hashmap to keep track of our characters.

#### Javascript

```javascript
var lengthOfLongestSubstring = function (s) {
  const mem = {};
  let windowStart = 0;
  let result = 0;
  for (let windowEnd = 0; windowEnd < s.length; windowEnd++) {
    let char = s[windowEnd];
    if (!(char in mem)) {
      mem[char] = 0;
    }
    mem[char]++;

    while (mem[char] > 1) {
      let removeChar = s[windowStart];
      mem[removeChar]--;
      if (mem[removeChar] === 0) {
        delete mem[removeChar];
      }
      windowStart++;
    }
    result = Math.max(result, windowEnd - windowStart + 1);
  }
  return result;
};
//OR using the index of the characters below:
var lengthOfLongestSubstring = function (s) {
  let windowStart = 0,
    maxLength = 0,
    charIndexMap = {};
  for (let windowEnd = 0; windowEnd < s.length; windowEnd++) {
    const rightChar = s[windowEnd];
    if (rightChar in charIndexMap) {
      windowStart = Math.max(windowStart, charIndexMap[rightChar] + 1);
    }
    charIndexMap[rightChar] = windowEnd;
    maxLength = Math.max(maxLength, windowEnd - windowStart + 1);
  }
  return maxLength;
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
