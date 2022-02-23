
## Question

Given an array arr of unsorted numbers and a target sum, count all triplets in it such that arr[i] + arr[j] + arr[k] < target where i, j, and k are three different indices. Write a function to return the count of such triplets.
Find count of triplets with sum smaller than given sum value

#### input:

Input: nums = [-2, 0, 1, 3] target = 2;

#### Output:

Output: 2, because [[-2, 0, 1],[-2, 0, 3]]

## Solution

To solve this we follow the same pattern as previously for the three sum problem, except this time we just increment our counter variable each time we reach a value where our sum of two pairs is greater than the target value.

#### Javascript

```javascript
const triplet_with_smaller_sum = function (arr, target) {
  count = 0;
  arr.sort((a, b) => a - b);
  for (let i = 0; i < arr.length - 2; i++) {
    if (i > 1 && arr[i] === arr[i - 1]) continue;
    let p1 = i + 1;
    count += helper(arr, p1, target - arr[i]);
  }

  return count;
};

const helper = (arr, p1, target_s) => {
  let p2 = arr.length - 1;
  let count = 0;
  while (p1 < p2) {
    let currentSum = arr[p1] + arr[p2];
    if (currentSum < target_s) {
      count += p2 - p1; //there can be total p2-p1 third elements.
      console.log(count);
      p1++;
    } else {
      p2--;
    }
  }
  return count;
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
