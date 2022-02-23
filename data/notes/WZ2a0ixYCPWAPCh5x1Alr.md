
Stacks contain data nodes, and they follow the principles of Last in First out(LIFO) order.

Stacks can be implemented using either an array or linked list, and support three main operations of adding data to the top of the stack, removing and providing data from top of the stack, and finally peek which reveals the data on top of the stack.

Stacks can also have a size limit, where if data is pushed into a full stack it will result in a stack overflow.

Real life situation of a stack is a line at a grocery store, where the first in line is checked out, and new comers are last in.

Below we can see that we can create a stack from a linked list, but we can also create a stack from an array as well.

```javascript
const LinkedList = require("./LinkedList");

class Stack {
  constructor(maxSize = Infinity) {
    this.stack = new LinkedList();
    this.maxSize = maxSize;
    this.size = 0;
  }

  hasRoom() {
    return this.size < this.maxSize;
  }

  isEmpty() {
    return this.size === 0;
  }

  push(value) {
    if (this.hasRoom()) {
      this.stack.addToHead(value);
      this.size++;
    } else {
      throw new Error("Stack is full");
    }
  }

  pop() {
    if (!this.isEmpty()) {
      const value = this.stack.removeHead();
      this.size--;
      return value;
    } else {
      throw new Error("Stack is empty");
    }
  }

  peek() {
    if (!this.isEmpty()) {
      return this.stack.head.data;
    } else {
      return null;
    }
  }
}
```
