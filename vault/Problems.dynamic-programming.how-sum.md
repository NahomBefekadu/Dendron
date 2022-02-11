---
id: vuKT7FsbEJKavKvmKOxyN
title: HowSum
desc: ""
updated: 1644256147405
created: 1644254141284
---

## Question

Given a target sum and an array of integers, return any combination of array elements that equals the target sum. if there is no combination the function should return null.
you can use an element of the array as many times as needed, and all elements are positive.

#### input:

target = 7;
array = [2,4]

#### Output:

output = Null

## Solution

As we have done previously we can visualize this problem in a form of a tree.
if we were given a target sum of 7, and an array which contains [5,4,3,7], we can visualize the problem as shown below.
![](/assets/images/2022-02-07-12-23-57.png)
As can be seen in the graph we have three ways of getting our target sum as we have nodes that reach 0.

#### Javascript

```javascript
function howSum(array, targetSum, mem = {}) {
  if (targetSum === 0) return [];
  if (targetSum < 0) return null;
  if (targetSum in mem) return mem[targetSum];
  for (const num of array) {
    const remainder = targetSum - num;
    var remainderResult = fourNumberSum(array, remainder, mem);
    if (remainderResult !== null) {
      mem[targetSum] = [...remainderResult, num];
      return mem[targetSum];
    }
  }
  mem[targetSum] = null;
  return mem[targetSum];
}
```

#### Java

```java

```

## Concepts
