
## Question

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The relative order of the elements may be changed.

#### input:

Input: nums = [3,2,2,3], val = 3

#### Output:

Output: 2, nums = [2,2,_,_]

## Solution

We can simply use two pointers again for this solution, we will have our first pointer iterate over the array, and have our second pointer point to elements which do not equal to our value. Then as we iterate through the array we move our values found in the array to the back of the array by swapping values in place.

#### Javascript

```javascript
var removeElement = function (nums, val) {
  let p2 = 0; // index of the next element which is not 'key'
  let p1 = 0;
  while (p1 < nums.length) {
    if (nums[p1] !== val) {
      nums[p2] = nums[p1];
      p2 += 1;
    }
    p1++;
  }
  return p2;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- Two Pointer
