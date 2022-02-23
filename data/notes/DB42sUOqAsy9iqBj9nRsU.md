
Linked Lists are Linear Data Structures that hold data in nodes, and where each element is arranged/stored sequentially. But they are also recursive data structures as linked lists are composed of smaller instances of themselves(nodes). The data they held by the node is composed of a value and a pointer to another node.

How do linked lists then differ from an array, well we know that in an array all the data has to be continuous in memory. But in the case of linked list all the data it contains do not have be next to each other in memory.

Single Linked List

```mermaid
graph TD;
A[value:A next:B] --> B[value:B next:null]

```

Doubly Linked List

```mermaid
graph TD;
A[value:A next:B previous:null] --> B[value:B next:null previous:A]
B[value:B next:null previous:A] --> A

```

When looking at the linked list we can see that it has an insertion of O(1) but comparatively worse look up time of (n). This look up time is related to the fact that you have to traverse the linked list to find the right insertion or lookup point. As to get the 50th element in a linked list, you would have to traverse 49 nodes from the head node to reach it.

## Traversal

Now we can traverse through a given linked lists two ways either iteratively or recursively. we can look at a simple function to print a given linked list.

```javascript
// iteratively
const printLinkedList = (head) => {
  current = head;
  while (current !== null) {
    console.log(current.data);
    current = current.next;
  }
};
//recursively
const PrintLinkedList = (head) => {
  current = head;
  if (current === null) return;
  console.log(current.data);
  PrintLinkedList(current.next);
};
```
