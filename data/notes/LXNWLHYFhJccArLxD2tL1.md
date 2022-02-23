
## Question

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.
You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
Once you reach a tree with fruit that cannot fit in your baskets, you must stop.
Given the integer array fruits, return the maximum number of fruits you can pick.

#### input:

Input: fruits = [1,2,3,2,2]

#### Output:

Output: 4

## Solution

To solve this we can use our SlidingWindow pattern as done previously, but we will be using a map to keep track of each fruit and how many fruits we currently have. As we go through the fruits we increment the count of fruit if it already exists in our map. But as the problem states we can only have two distinct fruits so we check our object against this each time.
Once we have gone over that, we decrement our object using our windowstart until we're below that treshold.
As we do this we are keeping the longest length of fruits we have in our basket.

#### Javascript

```javascript
const fruits_into_baskets = function (fruits) {
  const mem = {};
  let windowStart = 0;
  let result = 0;

  for (windowEnd = 0; windowEnd < fruits.length; windowEnd++) {
    fruit = fruits[windowEnd];
    if (!(fruit in mem)) {
      mem[fruit] = 0;
    }
    mem[fruit]++;
    while (Object.keys(mem).length > 2) {
      let removeFruit = fruits[windowStart];
      mem[removeFruit]--;
      if (mem[removeFruit] === 0) {
        delete mem[removeFruit];
      }
      windowStart++;
    }
    result = Math.max(result, windowEnd - windowStart + 1);
  }
  return result;
};
```

#### Java

```java

```

## Concepts

## Patterns
