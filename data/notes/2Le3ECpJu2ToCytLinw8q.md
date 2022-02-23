
## Question

Given a grid of 1s and 0s. where 0 represents water and 1 represents land. You should return the number of islands on the given grid.

definition of an island is a land vertically or horizontally connected.

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

Output: 1

## Solution

This is different from the format we've usually seen for our graphs, instead of an adjacency list we're given now a grid instead.

To solve this question we have two choices either depth-first or breadth-first. So we can solve this by iterating over the grid to move to each node, and at each point calling our depth first function. to iterate through and find an island at that particular point. If we find an island we return and increment our island counter.

When we go through our islands, we will still be using the same principles as before, making use of a set to keep track of all points visited by our function.

We first need a way to iterate through our given grid, and we can do that simply using two for loops, after that we will be calling our depth-first function at each point on the grid.

Within our depth-first function we set up the bounds of the given grid, so that when we run this function recursively, we are checking against the bounds we set, to see if the given point is valid. if it's not valid we can simply return false, same if the point we're checking is water or it has been visited before.

#### Javascript

```javascript
var numIslands = function (grid) {
  const visited = new Set();
  var count = 0;
  for (let row = 0; row < grid.length; row++) {
    for (let col = 0; col < grid[row].length; col++) {
      if (helper(grid, row, col, visited) === true) {
        count++;
      }
    }
  }

  return count;
};

const helper = (grid, row, col, visited) => {
  const rowBound = 0 <= row && row < grid.length;
  const colBound = 0 <= col && col < grid[0].length;
  if (!rowBound || !colBound) return false;

  if (grid[row][col] === "0") return false;

  const position = row + "," + col;
  if (visited.has(position)) return false;
  visited.add(position);

  helper(grid, row - 1, col, visited);
  helper(grid, row + 1, col, visited);
  helper(grid, row, col - 1, visited);
  helper(grid, row, col + 1, visited);

  return true;
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
