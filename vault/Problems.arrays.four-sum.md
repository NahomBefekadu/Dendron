---
id: RhpCJdLetWjrVSRoaJCYP
title: four-sum
desc: ''
updated: 1645418856730
created: 1645416518423
---

## Question

Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:

0 <= a, b, c, d < n
a, b, c, and d are distinct.
nums[a] + nums[b] + nums[c] + nums[d] == target
You may return the answer in any order.

#### input:

Input: nums = [1,0,-1,0,-2,2], target = 0

#### Output:

Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

## Solution

For our solution to this problem, we can base it off of our solution for our three sum problem.

#### Javascript

```javascript
var fourSum = function (arr, target) {
  quadruplets = [];
  arr.sort((a, b) => a - b);
  for (let i = 0; i < arr.length - 3; i++) {
    if (i > 0 && arr[i] === arr[i - 1]) continue;
    helper(arr, i, i + 1, target, quadruplets);
  }
  return quadruplets;
};
const helper = (arr, first, second, target, quadruplets) => {
  for (let i = second; i < arr.length - 2; i++) {
    if (i > second + 1 && arr[i] === arr[i - 1]) continue;
    let p1 = i + 1;
    let p2 = arr.length - 1;
    while (p1 < p2) {
      let currentSum = arr[first] + arr[i] + arr[p1] + arr[p2];
      if (currentSum === target) {
        quadruplets.push([arr[first], arr[i], arr[p1], arr[p2]]);
        while (arr[p1] === arr[p1 - 1]) p1++;
        while (arr[p2] === arr[p2 + 1]) p2--;
        p1++;
        p2--;
      } else if (currentSum < target) {
        p1++;
      } else {
        p2--;
      }
    }
  }
  return quadruplets;
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
