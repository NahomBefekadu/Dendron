---
id: dFBP44ODoPQpWeGUGeiDe
title: maximum-subarray-of-sizeK
desc: ""
updated: 1645158841820
created: 1644948426577
---

## Question

Given an array as input and k number, find the maximum sub of any contiguous subArray of size k.

#### input:

Input: [2, 1, 5, 1, 3, 2], k=3

#### Output:

Output: 9

## Solution

#### Javascript

```javascript
const max_sub_array_of_size_k = function (k, arr) {
  let maxSum = [];
  for (let i = 0; i < arr.length - k + 1; i++) {
    let currentSum = 0;
    for (let j = i; j < i + k; j++) {
      currentSum += arr[j];
    }
    maxSum.push(currentSum);
    console.log(maxSum);
  }
  return Math.max(...maxSum);
};

const slidingWindow = function (k, arr) {
  let maxSum = [];
  let windowSum = 0;
  let WindowStart = k;
  for (let windowEnd = 0; windowEnd < arr.length; windowEnd++) {
    windowSum += arr[windowEnd];
    if (windowEnd >= k - 1) {
      maxSum.push(windowSum);
      currentSum -= windowStart;
      windowStart++;
    }
    console.log(maxSum);
  }
  return Math.max(...maxSum);
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- sliding window
