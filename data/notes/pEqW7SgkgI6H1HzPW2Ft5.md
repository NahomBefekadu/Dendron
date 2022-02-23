
## Question

Given a binary array nums and an integer k, return the maximum number of consecutive 1's in the array if you can flip at most k 0's.

#### input:

Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2

#### Output:

Output: 6

## Solution

Here we can continue to use the sliding window pattern, but this time we don't need to use a set or map, as we only have two values binary bits 1 or 0.
So we just need to keep track of the maximum number of 1s in our window in a variable. So following previous patterns we can simply subtract the number of 1s in our window and check if the remaining 0s are greater than k. if so we shrink our sliding window.
As we do this we're also keeping track of the maximum number of contiguous subarray.

#### Javascript

```javascript
const length_of_longest_substring = function (arr, k) {
  // TODO: Write your code here
  let numRepeat = 0;
  let maxResult = 0;
  let windowStart = 0;

  for (let windowEnd = 0; windowEnd < arr.length; windowEnd++) {
    let p1 = arr[windowEnd];
    if (p1 === 1) {
      numRepeat++;
    }
    while (windowEnd - windowStart + 1 - numRepeat > k) {
      let p2 = arr[windowStart];
      if (p2 === 1) {
        numRepeat--;
      }
      windowStart++;
    }
    maxResult = Math.max(maxResult, windowEnd - windowStart + 1);
  }
  return maxResult;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- sliding window
