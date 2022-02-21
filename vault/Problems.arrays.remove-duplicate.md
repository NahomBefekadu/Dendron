---
id: G24vKJQblZsOfAc7g549D
title: remove-duplicate
desc: ""
updated: 1645393564707
created: 1645393056323
---

## Question

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

#### input:

Input: nums = [1,1,2]

#### Output:

Output: 2, nums = [1,2,_]

## Solution

We can use our two pointer pattern to find a solution here, We will first initialize our two pointers to the second element of the array.
Then we can do a simple while loop to iterate over the array, and as we go through the array we check if our current element is not a duplicate. If it is not a duplicate we make our the value that our second pointer is at equal to the element that our first pointer is at. This way we move elements that are not duplicate in the first half of the array. If we find that the element is a duplicate we simply keep incrementing our first pointer until we find a unique element to swap values.

#### Javascript

```javascript
const remove_duplicates = function (arr) {
  let p1 = 1;
  let p2 = 1;
  let count = 1;
  while (p1 < arr.length) {
    if (arr[p1] !== arr[p2 - 1]) {
      arr[p2] = arr[p1];
      count++;
      p2++;
    }
    p1++;
  }

  return count;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- Two Pointers
