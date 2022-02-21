---
id: Fvlig9pSrEWx8pdT9DYG3
title: three-sum-closest
desc: ""
updated: 1645410808622
created: 1645408087709
---

## Question

Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.

#### input:

Input: nums = [-1,2,1,-4], target = 1

#### Output:

Output: 2

## Solution

This is exactly the same as our previous solution for three sum problem, but this time we sill save the sum of each value and return the smallest sum value at the end.
As done previously, we will first sort our array, then we will iterate through our array.

at each current value we go through a while loop to check for possible combinations of values to find the smallest sum value, if we find a combination that is equal to our target sum or it's difference is 0. we can simply return this value. Otherwise for each combination sum we check it with our current smallest value, and save it if it's smaller than our current smallest sum.

#### Javascript

```javascript
var threeSumClosest = function (arr, target_sum) {
  let smallestSum = Infinity;
  arr.sort((a, b) => a - b);
  for (let i = 0; i < arr.length - 2; i++) {
    let p1 = i + 1;
    let p2 = arr.length - 1;
    while (p1 < p2) {
      let targetDiff = target_sum - arr[i] - arr[p1] - arr[p2];
      if (targetDiff === 0) {
        return target_sum;
      }

      if (Math.abs(targetDiff) < Math.abs(smallestSum)) {
        smallestSum = targetDiff;
      }

      if (targetDiff > 0) {
        p1++;
      } else {
        p2--;
      }
    }
  }
  return target_sum - smallestSum;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]
- [[Problems.arrays.three-number-sum]]

## Patterns

- Two Pointer
