---
id: CfJ8vN1e40PJUPWEOG8Ql
title: two-sum
desc: ""
updated: 1645407866471
created: 1645406913224
---

## Question

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.

Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.

The tests are generated such that there is exactly one solution. You may not use the same element twice.

Your solution must use only constant extra space.

#### input:

Input: numbers = [2,7,11,15], target = 9

#### Output:

Output: [1,2]

## Solution

This question comes in different varieties, it might be sorted or not sorted, and might ask for index values or the actual values as well. But the solution stays the same only what you return is different. Now we can solve this using two ways, one is simpler and easier than other.

The first way we will solve this is using hashmaps, and then we will solve it using two pointers( as it is already sorted).

For our first way, we can simply subtract from target sum our current value and check if the result is in our hashmap. As A+B = X, A=X-B. Thus, if it's not in our map we simply add it to our hashmap and keep iterating through our array.

For our second solution, as our array is already sorted we can use two pointers, one at both ends of the array. Then we can increment from both sides until we find a value which matches our target. We will increment our value depending on the value of our current sum, if the current sum is greater than our target value we need to decrease our current value. So we will decrease our pointer at the end of our array and if it's less than our target value then we need to increase our value. Therefore we increase our pointer to the left of the array. If the array is not sorted we would need to sort it, which means that we would add an O(nlog(n)) complexity to our solution.

#### Javascript

```javascript
var twoSum = function (numbers, target) {
  const previousNums = {};
  for (let i = 0; i < numbers.length; i += 1) {
    const num = numbers[i];
    const complement = target - num;
    if (complement in previousNums)
      return [previousNums[complement] + 1, i + 1];

    previousNums[num] = i;
  }
};
//Or
var twoSum = function (numbers, target) {
  let p1 = 0;
  let p2 = numbers.length - 1;
  while (p1 < p2) {
    let current_Sum = numbers[p1] + numbers[p2];
    if (current_Sum === target) {
      return [p1 + 1, p2 + 1];
    } else if (current_Sum < target) {
      p1++;
    } else {
      p2--;
    }
  }
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- Two Pointers
- HashMap
