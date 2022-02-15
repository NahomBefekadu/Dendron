---
id: WouSjAvULx6Qu2G2YzCOp
title: Minimum Island
desc: ""
updated: 1644895291763
created: 1643736241857
---

## Question

Given a grid containing 1s and 0s, where 0 represents water and 1 represents land. return the smallest island within the grid.

There is at least one island in the grid.

#### input:

```javascript
grid = [
  ["1", "1", "1", "1", "0"],
  ["1", "1", "0", "1", "0"],
  ["1", "1", "0", "0", "0"],
  ["0", "0", "0", "0", "0"],
];
```

#### Output:

minSize = num;

## Solution

Here we follow the same pattern as the island count, but instead of returning boolean values we return the size of the given island.

#### Javascript

```javascript
var minIsland = function (grid) {
  const visited = new Set();
  var min = 0;
  for (let row = 0; row < grid.length; row++) {
    for (let col = 0; col < grid[row].length; col++) {
      const size = helper(grid, row, col, visited);
      if (size > 0) min = Math.min(size, min);
    }
  }

  return min;
};

var helper = function (grid, row, col, visited) {
  const rowBound = 0 <= row && row < grid.length;
  const colBound = 0 <= col && col < grid[0].length;
  if (!rowBound || !colBound) return 0;

  if (grid[row][col] === "0") return 0;
  const position = row + "," + col;
  if (visited.has(position)) return 0;
  visited.add(position);
  let currentSize = 1;
  currentSize += helper(grid, row - 1, col, visited);
  currentSize += helper(grid, row + 1, col, visited);
  currentSize += helper(grid, row, col - 1, visited);
  currentSize += helper(grid, row, col + 1, visited);
  return currentSize;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.Graphs]]
- [[data-structures.Graphs.traverse]]

## Patterns

- DFS
- Set/Map
