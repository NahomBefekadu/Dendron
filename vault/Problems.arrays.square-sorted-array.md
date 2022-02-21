---
id: ZYm8WYwxGH6HXuZRUhFop
title: square-sorted-array
desc: ""
updated: 1645398439997
created: 1645397616513
---

## Question

Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

#### input:

Input: nums = [-4,-1,0,3,10]

#### Output:

Output: [0,1,9,16,100]

## Solution

We can solve this easily by brute forcing a solution by first squaring our array and then sorting it using a function of the language program, as seen in the first solution. But this is not the optimal solution, as it adds an O(nlog(n)) complexity to our solution. What we can do is use two pointers one at each end and compare the resulting square of both numbers to fill our squares array in order, starting from the highest value in our sorted square array.

#### Javascript

```javascript
const sortedSquares = function (arr) {
  squares = [];
  console.log(arr);
  for (let i = 0; i < arr.length; i++) {
    squares.push(arr[i] * arr[i]);
  }
  squares.sort((a, b) => a - b);
  return squares;
};
// OR
const sortedSquares = function (arr) {
  squares = new Array(arr.length).fill(0);
  let p1 = 0;
  let p2 = arr.length - 1;
  let highestValue = p2;
  while (p1 <= p2) {
    let leftValue = arr[p1] * arr[p1];
    let rightValue = arr[p2] * arr[p2];
    if (rightValue > leftValue) {
      squares[highestValue] = rightValue;
      p2--;
    } else {
      squares[highestValue] = leftValue;
      p1++;
    }
    highestValue--;
  }
  return squares;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- Two Pointer
