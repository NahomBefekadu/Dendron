
## Question

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

#### input:

Input: nums = [-1,0,1,2,-1,-4]

#### Output:

Output: [[-1,-1,2],[-1,0,1]]

## Solution

For our three sum solution, we can first sort our array, then attempt to solve this. As sorting our array would take less time than finding the solution( the added complexity can be ignored).

The way in which we can solve this is by implementing the solution of a two sum problem into this, As our array is sorted we put our first pointer as the next one in to this value, and send it to our two sum helper function as the target value. Because A+B+C=0, so -C=A+B. Therefore we send to our two sum function our array, first pointer, target value and our triplet array.

In our Two Sum function we can approach this using two pointers instead of using sets as done previously. we will have our second pointer pointing to the end of our array, and do a while loop. In our while loop we check if the sum of the two values of our pointer is equal to our target value. If it equals the target value we can simply push it into our triplets array the three values needed, and increment our pointers. As we need to avoid having duplicate triplets, we do another while loop inside our if statement to skip same elements for both our pointers.

If our current sum does not equal our target value then we can simply increase our pointers. If our current sum is less than the target sum we need a bigger current sum, so we increment our first pointer, and vice versa for our second pointer. Once we have tried all combination we simply return our triplet array. In our original array before we call our helper function we also need to check if we have the same element and skip it in order to avoid duplicate triplets in our triplets array.

#### Javascript

```javascript
var threeSum = function (arr) {
  triplets = [];
  arr.sort((a, b) => a - b);
  for (let i = 0; i < arr.length; i++) {
    if (i > 0 && arr[i] === arr[i - 1]) {
      continue;
    }
    help(arr, i + 1, -arr[i], triplets);
  }
  return triplets;
};
const help = (arr, p1, target_Sum, triplets) => {
  let p2 = arr.length - 1;
  while (p1 < p2) {
    currentSum = arr[p1] + arr[p2];
    if (currentSum === target_Sum) {
      triplets.push([-target_Sum, arr[p1], arr[p2]]);
      p2--;
      p1++;
      while (arr[p1] === arr[p1 - 1]) p1++;
      while (arr[p2] === arr[p2 + 1]) p2--;
    } else if (currentSum < target_Sum) {
      p1++;
    } else {
      p2--;
    }
  }
  return triplets;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]
- [[Problems.arrays.two-sum]]

## Patterns

- Two Pointer
