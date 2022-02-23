
## Question

Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

#### input:

Input: nums = [2,0,2,1,1,0]

#### Output:

Output: [0,0,1,1,2,2]

## Solution

To solve this we will have two pointers one at each end of the array, then we have a simple while loop in place. In the while loop we check if the current value we're at is equal to 0, if so we swap values on the spot with our left pointer and increment our left pointer and i. We do the same if we find that our current value is equal to 2, we swap it with that value and decrement our right pointer. if it doesn't meet these two conditions it's a one so we simply just increment i.

#### Javascript

```javascript
var sortColors = function (arr) {
  let p1 = 0,
  let i = 0;
  let p2 = arr.length - 1;
  while (i <= p2) {
    if (arr[i] === 0) {
      [arr[i], arr[p1]] = [arr[p1], arr[i]];
      i++;
      p1++;
    } else if (arr[i] === 2) {
      [arr[i], arr[p2]] = [arr[p2], arr[i]];
      p2--;
    } else {
      i++;
    }
  }
  return arr;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- Two Pointer
