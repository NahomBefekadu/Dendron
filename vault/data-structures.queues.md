---
id: bp7DKWzognTMTV0zzhTat
title: Queues
desc: ""
updated: 1641702468633
created: 1641702465917
---

Queues can be implemented using various data structures the main one being singly linked lists. Queues contain data nodes and have three modes of operations. Queues operate on the principle of FIFO which is first in first out.

Enqueue adds data to the back of the queue, Dequeue removes and provides the data from the front of the queue, and lastly peek provides the data on the front of the queue

When working with queues Enqueueing onto a full queue would causes a queue overflow to occur. In the opposite cause dequeuing data from an empty queue can cause an underflow to occur.

Bonded queues also have a limited size, they are queues which limit the number of nodes they can have. as for other methods of employing a queue an array can be used to implement one as well.

Below you can see two example queues where one has a maximum size and the other one is a simpler implementation of queues.

```javascript
const LinkedList = require("./LinkedList");

class Queue {
  constructor() {
    this.queue = new LinkedList();
    this.size = 0;
  }

  enqueue(data) {
    this.queue.addToTail(data);
    this.size++;
    console.log(`Added ${data} to queue! Queue size is now ${this.size}.`);
  }

  dequeue() {
    const data = this.queue.removeHead();
    this.size--;
    console.log(`Removed ${data} from queue! Queue size is now ${this.size}.`);
    return data;
  }
}

module.exports = Queue;
```

```javascript
const LinkedList = require("./LinkedList");

class Queue {
  constructor(maxSize = Infinity) {
    this.queue = new LinkedList();
    this.maxSize = maxSize;
    this.size = 0;
  }

  isEmpty() {
    return this.size === 0;
  }

  hasRoom() {
    return this.size < this.maxSize;
  }

  enqueue(data) {
    if (this.hasRoom()) {
      this.queue.addToTail(data);
      this.size++;
      console.log(`Added ${data} to queue! Queue size is now ${this.size}.`);
    } else {
      throw new Error("Queue is full!");
    }
  }

  dequeue() {
    if (!this.isEmpty()) {
      const data = this.queue.removeHead();
      this.size--;
      console.log(
        `Removed ${data} from queue! Queue size is now ${this.size}.`
      );
      return data;
    } else {
      throw new Error("Queue is empty!");
    }
  }
}

module.exports = Queue;
```
