
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

## LinkedList

This is our class created for our linked list, we first create a constructor and set our head value for our linked list to **null**

```javascript
class LinkedList {
  constructor() {
    this.head = null;
  }
}
```

#### Adding

After that we need a way in which we can add a new node and data into our created linked list, so we create a method to create a set of nodes.

The add to head method works by first creating a new Node using the module we imported and created previously, from there we create a variable to hold the current head state of the linked list and set that to **this.head** which refers to the object created.

As we are adding a new node to our head we need to set our currenthead in our list as the NextNode to the new value being added in, essentially our new node pushes the current head down so that there is something new pointing to it.

```javascript
addToHead(data) {
    const newHead = new Node(data);
    const currentHead = this.head;
    this.head = newHead;
    if (currentHead) {
      this.head.setNextNode(currentHead);
    }
  }
```

We have our method to add a new node into the head of our linked list but linked lists can also add a new node from the tail of a linked list so we need to create a similar method for adding to the tail.

When we add a new node to our tail we first check if there is any node value currently, if not we set our new node at that location if not we loop through our linked list until we have reached the point where the currentnode we're at has a null value for its next node at that point we create a new node at that point, with the current node we're on pointing to that node. This is because this data structure only keeps track of the head of the list hence the need to traverse this list to add to the tail.

```javascript
addToTail(data) {
    let tail = this.head;
    if (!tail) {
      this.head = new Node(data);
    } else {
      while (tail.getNextNode() !== null) {
        tail = tail.getNextNode();
      }
      tail.setNextNode(new Node(data));
    }
  }
```

#### Removing

We have our two methods for adding new nodes into our list but we now need a method to remove a node from the list.

when we remove a node, we first set a variable to hold the currentNode, and we first check if there is anyvalue at that current node, if there is no value we return from our function. if not we set the current head to the nextnode of the current node and return the data.

```javascript
 removeHead() {
    const removedHead = this.head;
    if (!removedHead) {
      return;
    }
    this.head = removedHead.getNextNode();
    return removedHead.data;
  }
```

we can also add a method to be able to see our whole linked list in one command, thats the method for printList it removes the need to have multiple console log methods to print your linked list every time its updated.

#### Print

```javascript
  printList() {
    let currentNode = this.head;
    let output = '<head> ';
    while (currentNode !== null) {
      output += currentNode.data + ' ';
      currentNode = currentNode.getNextNode();
    }
    output += '<tail>';
    console.log(output);
  }
```

## Example of Linked Lists

we have created the necessary classes to implement a LinkedList now we can use those classes to create a linked list by creating an instance of that class.

our first example consists of creating a simple stringed list of "one" "two" etc.. and we will use the tools to build a list of these string values

```javascript
const LinkedList = require("./LinkedList");

const Numbers = new LinkedList();
Numbers.printList();
Numbers.addToHead("One");
Numbers.addToHead("Two");
Numbers.printList();
Numbers.addToTail("Three");
Numbers.addToTail("Four");
Numbers.printList();
Numbers.removeHead();
Numbers.printList();

/*
The out put of this function will be 
<head> <tail>
<head> Two One <tail>
<head> Two One Three Four <tail>
<head> One Three Four <tail>

*/
```
