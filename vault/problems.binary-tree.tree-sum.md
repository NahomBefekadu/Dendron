---
id: SimMK6mMAWR4H53Xqh9XB
title: Tree Sum
desc: ""
updated: 1644895790756
created: 1644728135283
---

## Question

Given a root of a tree, return the total sum of all values in the binary tree.

#### input:

```mermaid
graph TD;
    1-->3;
    1-->2;
    2-->6;
    2-->7;
    3-->4;
    3-->8;
```

#### Output:

## Solution

we can solve this by traversing through the graph and adding all our values as we go.

This can be done either through DFS (pre,post,in) or BFS.

#### Javascript

```javascript
const treeSum = (root) => {
  if (root === null) return 0;
  return root.val + treeSum(root.left) + treeSum(root.right);
};
```

#### Java

```java

```

## Concepts

- [[data-structures.recursion]]
- [[data-structures.binary-trees]]
- [[data-structures.binary-trees.traverse]]

## Patterns

- DFS
