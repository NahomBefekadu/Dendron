---
id: T4qw6hGr3CTLuWfyAcBHO
title: grid-traveler
desc: ""
updated: 1644896085571
created: 1644246871096
---

## Question

Given a grid size of m by n, starting at the most left corner how many ways can you reach the bottom right corner of the grid.

You can only travel down or right through the grid.

#### input:

grid(2,3);

#### Output:

possible moves: 3

## Solution

To complete this lets first visualize the problem.
![](/assets/images/2022-02-07-10-14-43.png)

As seen in the graph below if were given a grid of 3 by 3. we can see all the possible moves that we can make to reach the end of the grid. We can also see we have locations that keep repeating, thus what we can do is similar to our fibonacci solution where we can save the return statement(value) of that given point in our function. reducing the steps needed to reach the end of the grid.

#### Javascript

```javascript
const gridTraveler = (m, n, mem = {}) => {
  if (m === 1 && n === 1) return 1;
  if (m === 0 || n === 0) return 0;
  var position = m + "," + n;
  if (position in mem) return mem[position];
  mem[position] = gridTraveler(m - 1, n, mem) + gridTraveler(m, n - 1, mem);
  return mem[position];
};

console.log(gridTraveler(18, 18));
//2333606220
// O (m*n) Time
// O(m+n) space
```

#### Java

```java

```

## Concepts

[[data-structures.recursion]]

## Patterns

- Map/Set
