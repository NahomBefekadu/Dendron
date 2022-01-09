---
id: a7n7Z1pfmMiPOqzs3RlAw
title: Double Linked List
desc: ""
updated: 1641702299539
created: 1641700925160
---

# Linked Lists

In javascript Linked lists use the Node class, which can also be imported from Node.js

Below is the structure for a Node class that can be used to create linked lists.

**this.next** property is used to keep track of the following node.

**this.data** property is used to hold the data of the node.

## Node

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }

  setNextNode(node) {
    if (node instanceof Node || node === null) {
      this.next = node;
    } else {
      throw new Error("Next node must be a member of the Node class.");
    }
  }

  getNextNode() {
    return this.next;
  }
}
```

we can use this Node class to create a list of nodes connected with each other and we can do that by creating a node and setting its next node property.

```javascript
const FirstNode = new Node('I"m first node');
const SecondNode = new Node('I"m second node');
const ThirdNode = new Node('I"m third node');

FirstNode.setNextNode(SecondNode);
SecondNode.setNextNode(ThirdNode);
```

so when creating a linked list we would go about first importing the Node class.

```javascript
const Node = require("./Node");
```

So that's the base structure for a Node now how do we go about creating a linked list, first as stated above we call our Node module created previous and we create a LinkedList class.

## Doubly Linked Lists

Similar to linked lists doubly linked lists comprise of nodes as well, the change is that they contain two pointer now which point to the next node similar to a linked list and a new addition a pointer to the previous node.

previously when we created our next node it was pointing to null similarly for our previous node it will point to null as well , this is useful as doubly linked lists make traversal of the list easier.

a bus route is similar to a doubly linked list with its stops serving as nodes, you can start from the head node and go down to the end of the stop and take the bus in reverse to go back to the starting point.

### Node

this is the node class which we will use to create our doubly linked list, it's similar to the previous node but we've added the functionality of previous pointer.

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
    this.previous = null;
  }

  setNextNode(node) {
    if (node instanceof Node || node === null) {
      this.next = node;
    } else {
      throw new Error("Next node must be a member of the Node class");
    }
  }

  setPreviousNode(node) {
    if (node instanceof Node || node === null) {
      this.previous = node;
    } else {
      throw new Error("Previous node must be a member of the Node class");
    }
  }

  getNextNode() {
    return this.next;
  }

  getPreviousNode() {
    return this.previous;
  }
}

module.exports = Node;
```

#### Adding

When we add nodes to doubly linked list we have to take care and keep track of the two pointers we now have.

if we are adding to the head of the list we need to first check as always if there is a current head to the list, if there's none it becomes simple we just add a node where both the pointers are set to null. If not then we have to set the **current heads** previous pointer to our **new head** and set the next pointer of our **new head** to the **current head**, and we set the **new head**'s previous pointer to null.

if we are adding to the tail similar to the head we check if list is empty following the same process as the head, if its not empty we set the current **tails** next pointer to the **new tail**, set the **new tail** previous to the **current tail**, and set the **new tails** next pointer to null.

Add to Head:

```javascript
 addToHead(data){
    const newHead= new Node(data);
    const currentHead=this.head;
    if (currentHead){
      currentHead.setPreviousNode(newHead);
      newHead.setNextNode(currentHead);
    }
    this.head=newHead;
    if (!this.tail){
      this.tail=newHead;
    }
  }

```

Add to Tail:

```javascript
  addToTail(data){
    const newTail = new Node(data);
    const currentTail = this.tail;
    if (currentTail){
      currentTail.setNextNode(newTail);
      newTail.setPreviousNode(currentTail);
    }
    this.tail=newTail;
    if(!this.head){
      this.head=newTail;
    }
  }

```

#### Removing

when removing the head we have to set the previous pointer of the new head to null. if we are removing the tail we have to set the next pointer of the new tail to null. if there was only one single element in the list both processes will occur.

Now with double linked list we can remove a node from the middle of the list, that's one of the benefits. To do that we must set the removed nodes previous pointer to the following node after it, and we also must set the next node of the perceding node to its preceeding node.

For better clarity if B is removed we set the previous pointer of C from B to A, and we set the next pointer of A from B to C.

A <-> B <-> C

A <-> C

Remove from Head:

```javascript
removeHead() {
    const removedHead = this.head;
    if (!removedHead) {
      return;
    }
    this.head = removedHead.getNextNode();
    if (this.head) {
      this.head.setPreviousNode(null);
    }
    if (removedHead === this.tail) {
      this.removeTail();
    }
    return removedHead.data;
  }

```

Remove from Tail:

```javascript
  removeTail() {
    const removedTail = this.tail;
    if (!removedTail) {
      return;
    }
    this.tail = removedTail.getPreviousNode();
    if (this.tail) {
      this.tail.setNextNode(null);
    }
    if (removedTail === this.head) {
      this.removeHead();
    }
    return removedTail.data;
  }
```

#### Removing using Data

we first have to find a way to find the data we want to remove within our list, so the code below shows exactly that.

```javascript
  removeByData(data){
    let nodeToRemove;
    let currentNode = this.head;
    while(currentNode){
      if (currentNode.data===data){
        nodeToRemove=currentNode;
        break;
      }
      currentNode=currentNode.getNextNode();
    }
    if (!nodeToRemove){
      return null;
    }
  }
```

now that we have found our given node that we would like to remove we have to remove it from our list, so we add to the code we already have from before.

```javascript
removeByData(data) {
    let nodeToRemove;
    let currentNode = this.head;
    while (currentNode !== null) {
      if (currentNode.data === data) {
        nodeToRemove = currentNode;
        break;
      }
      currentNode = currentNode.getNextNode();
    }
    if (!nodeToRemove) {
      return null;
    }

    if(nodeToRemove===this.head){
      this.removeHead();
    }else if (nodeToRemove===this.tail){
      this.removeTail();
    }else{
      const nextNode = nodeToRemove.getNextNode();
      const previousNode=nodeToRemove.getPreviousNode();
      nextNode.setPreviousNode(previousNode);
      previousNode.setNextNode(nextNode);
    }
    return nodeToRemove;

  }
```

## Example of Doubly Linked Lists

```javascript
const DoublyLinkedList = require("./DoublyLinkedList.js");

const Bus = new DoublyLinkedList();

Bus.addToHead("Stop 3");
Bus.addToHead("Stop 2");
Bus.addToHead("Stop 1");
Bus.printList();

Bus.addToTail("Stop 4");
Bus.addToTail("Stop 5");
Bus.addToTail("Stop 6");
Bus.printList();

Bus.removeHead();
Bus.removeTail();
Bus.printList();

Bus.removeByData("Stop 4");
Bus.printList();

/*
OutPut:

<head> Stop 1 Stop 2 Stop 3 <tail>
<head> Stop 1 Stop 2 Stop 3 Stop 4 Stop 5 Stop 6 <tail>
<head> Stop 2 Stop 3 Stop 4 Stop 5 <tail>
<head> Stop 2 Stop 3 Stop 5 <tail>
*/
```
