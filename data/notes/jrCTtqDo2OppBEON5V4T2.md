
## Question

given an array and a target sum, return true if there is a combination of two numbers that equal the target.

you can use an element of the array as many times as needed, and all elements are positive.

#### input:

target = 3;
array =[4,2,1,5]

#### Output:

output = true;

## Solution

#### Javascript

```javascript
const canSum = (target, array, mem = {}) => {
  if (target === 0) return true;
  if (target < 0) return false;
  if (target in mem) return mem[target];
  for (const num of array) {
    const remainder = target - num;
    if (canSum(remainder, array, mem) === true) {
      mem[target] = true;
      return mem[target];
    }
  }
  mem[target] = false;
  return mem[target];
};
/*
m = target sum, and n = length of array.
brute force approach gives us O(n^m) time complexity and O(m) space complexity
for this memoization approach we have
O(m*n) time complexity
O(m) space complexity
*/
```

#### Java

```java

```

## Concepts

[[data-structures.recursion]]

## Patterns

- Map/Set
