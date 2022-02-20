---
id: SWb2YMdepwC0W96jXocde
title: smallest-subarray-with-greater-sum
desc: ""
updated: 1645158852097
created: 1645131265476
---

## Question

Given an array of integers, find the length of the smallest contiguous subarray where the sum is greater than or equal to S.

#### input:

Input: [2, 1, 5, 2, 3, 2], S=7

#### Output:

Output: 2

## Solution

We can approach this problem by using the sliding window pattern, but compared to the previous implementations here we have to dynamically change the size of the window as we progress.

We first start incrementing the windowEnd until we have a sum value which is greater than or equal to S. Once we reach that point we take the length of the array by substracting our window end and start.

We then increment our windowStart, and subtract that value from our current sum. Then we continue this process to get new lengths and comparing that length to our previous length and storing the smallest length to return.

#### Javascript

```javascript
const smallest_subarray_sum = function (s, arr) {
  let windowStart = 0;
  let windowSum = 0;
  let minLength = Infinity;
  for (windowEnd = 0; windowEnd < arr.length; windowEnd++) {
    windowSum += arr[windowEnd];
    while (windowSum >= s) {
      minLength = Math.min(minLength, windowEnd - windowStart + 1);
      windowSum -= arr[windowStart];
      windowStart++;
    }
    console.log(windowSum);
  }
  if (minLength === Infinity) {
    return 0;
  }
  return minLength;
};

//while loop would only run once so O(N+N)= O(N)
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- sliding window
