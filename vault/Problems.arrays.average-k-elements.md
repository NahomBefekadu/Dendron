---
id: l0AXctxDXCVzD7tOH8cot
title: average-k-elements
desc: ""
updated: 1644949825429
created: 1644947281703
---

## Question

Given an array and k, calculate the average of all subarrays of k contiguous elements.

#### input:

Array: [1, 3, 2, 6, -1, 4, 1, 8, 2], K=5

#### Output:

Output: [2.2, 2.8, 2.4, 3.6, 2.8]

## Solution

given this array we can use simply two loops to iterate over the array and calculate the 5 element subarray and divide the sum by k to get the average.

Another way to approach this is to use our sliding window pattern to solve this question.

#### Javascript

```javascript
const bruteForce = (arr, k) => {
  const result = [];
  for (let i = 0; i < arr.length - k + 1; i++) {
    let currentSum = 0;
    for (let j = i; j < i + k; j++) {
      currentSum += arr[j];
    }
    result.push(currentSum / 5);
  }
  return result;
};

const SlideWindow = (arr, k) => {
  const result = [];
  let windowSum = 0;
  let windowStart = 0;
  for (let windowEnd = 0; windowEnd < arr.length; windowEnd++) {
    windowSum += arr[windowEnd];
    if (windowEnd >= k - 1) {
      result.push(windowSum / 5);
      windowSum -= arr[windowStart];
      windowStart++;
    }
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

- Sliding Window
