
## Question

You are given a string s lowercase letters only, and an integer k. You can choose any character of the string and change it to any other lowercase English character. You can perform this operation at most k times.

you are allowed to replace no more than k letters with any letter

#### input:

Input: s = "aababba", k = 1

#### Output:

Output: 4

## Solution

Here we will be using our sliding window pattern to solve this, and a hash map to keep track of our characters. As we go through our array we will be also keeping count of number of times a character is repeated in our window. Then we can use this number and substract it from the window we currently have against our given k value. if the number is larger we know we cant replace the characters we have thus we have to shrink our window. We also take note of the length of the window and save it to our result. we keep repeating this throughout the whole string and return our longest substring.

#### Javascript

```javascript
const length_of_longest_substring = function (str, k) {
  let windowStart = 0;
  let mem = {};
  let max = 0;
  let numOfChar = 0;
  for (windowEnd = 0; windowEnd < str.length; windowEnd++) {
    char = str[windowEnd];
    if (!(char in mem)) {
      mem[char] = 0;
    }
    mem[char]++;
    numOfChar = Math.max(numOfChar, mem[char]);
    while (windowEnd - windowStart + 1 - numOfChar > k) {
      let removeChar = str[windowStart];
      mem[removeChar]--;
      if (mem[removeChar] === 0) {
        delete mem[removeChar];
      }
      windowStart++;
    }
    max = Math.max(max, windowEnd - windowStart + 1);
  }
  return max;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- Sliding Window
- Map/Set
