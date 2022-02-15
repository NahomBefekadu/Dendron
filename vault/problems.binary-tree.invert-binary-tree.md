---
id: g2pgFdlRqFmBGZAx2w5TX
title: Invert Binary Tree
desc: ""
updated: 1644895689047
created: 1641237469394
---

## Question

Given a Binary Tree, invert it.

#### input:

```mermaid
graph TD;
    1-->3;
    1-->2;
    2-->6;
    2-->7;
    3-->4;
    3-->8;
    8-->10;
```

#### Output:

```mermaid
graph TD;
    1-->2;
    1-->3;
    2-->6;
    2-->7;
    3-->4;
    3-->8;
    8-->10;
```

## Solution

#### Javascript

```javascript
function invertBinaryTree(tree) {
  // Write your code here.
  return helper(tree);
}
function helper(tree) {
  if (!tree) {
    return;
  }
  if (!tree.left && !tree.right) {
    return;
  }
  let temp = tree.left;
  tree.left = tree.right;
  tree.right = temp;
  helper(tree.left);
  helper(tree.right);
}

// This is the class of the input binary tree.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}
```

#### Java

```java
import java.util.*;

class Program {
  public static void invertBinaryTree(BinaryTree tree) {
		helper(tree);
  }
	public static void helper (BinaryTree node){
		if (node == null){
			return;
		}
		BinaryTree temp = node.left;
		node.left = node.right;
		node.right = temp;
		helper(node.left);
		helper(node.right);
	}

  static class BinaryTree {
    public int value;
    public BinaryTree left;
    public BinaryTree right;

    public BinaryTree(int value) {
      this.value = value;
    }
  }
}
```

## Concepts

- [[data-structures.binary-trees.traverse]]
- [[data-structures.recursion]]

## Patterns

- DFS
