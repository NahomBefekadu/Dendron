---
id: cbtfKehIOTrO5jfNiIp9f
title: fibonacci
desc: ""
updated: 1644895421134
created: 1644245078554
---

## Question

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
Given n, calculate F(n).

0 <= n <= 100

#### input:

F(0)

#### Output:

output = 0

## Solution

We cant do a simple recursion as done previously for our solution. our given n might be 50, 60 or higher. That means that our function will have to recursively step through way over million steps to complete. Thus we need to implement Memoization to save some answers to our sub problems.

if we look at the fibonacci graph below we can see that the sub tree of 3 occurs twice once on the right and on the left. That means if we save the return value of 3 on our first run every time we face a similar node we can simply return that value.

![](/assets/images/2022-02-07-09-56-32.png)

#### Javascript

```javascript
var fib = function (n, mem = {}) {
  if (n in mem) return mem[n];
  if (n === 0) return 0;
  if (n === 1 || n <= 2) return 1;

  mem[n] = fib(n - 1, mem) + fib(n - 2, mem);
  return mem[n];
};
```

#### Java

```java

```

## Concepts

- [[data-structures.recursion]]

## Patterns

- Set/Map
