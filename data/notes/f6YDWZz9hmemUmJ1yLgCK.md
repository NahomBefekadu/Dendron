
Hash maps map keys to the corresponding values, and is a very efficient way to retrieve stored data. The keys stored allow for this fast lookup time. Thus hash maps are useful data structure for problems which require storing and retrieving data.

Hash maps are built on top of arrays with a special index system, hash maps accomplish this by using a hash function which turns a key into an index for the array. The hash function.

Sometimes a hash function can give the same index for two different keys when that occurs a hash collision happens. There are two strategies to solve this one of them is separate chaining, where it avoids collisions by updating the underlying data structure. Instead of an array of values that are mapped to by hashes, it could be an array of linked lists! where each array index points to a different data structure and open addressing, to distinguish between different keys we store the the keys and values in the linked lists.

The down sides of separate chaining is that if the hash function gives the same key multiple times growing the linked list for the given key thus increasing the lookup time. This can be seen in the image below.

![](/assets/images/2022-01-09-20-49-39.png)

Another strategy is open addressing. In this case we don't use a linked list as the underlying data structure but stick to arrays. But instead when we receive the same key we instead look for a different index to save our data until an empty index is present. Meaning that if our probing sequence is set to 2 we increment the given key value by 2 until an empty index is present.

For example below if we want to insert the value 8 in our function and it gives us 4 as the key there is a collision, but since we set our probe to two it will increment key value by 2 until we find an empty index.

```terminal
   Index values
    0    1      2    3    4    5     6    7
[ null, null, null, null, 14, null, 36, null]
                          4 = collision
                                    3+2 = collision
        (6+2)-7=1 = no collision set value


```

There are other strategies available for dealing with collisions but they can get very complex, and even the hash function shown already can cause problems such as clustering. Which is what happens when a collision causes more collisions.

- **Hash map**: A key-value store that uses an array and a hashing function to save and retrieve values.
- **Key**: The identifier given to a value for later retrieval.
- **Hash function**: A function that takes some input and returns a number.
- **Compression function**: A function that transforms its inputs into some smaller range of possible outputs.

![](/assets/images/2022-01-09-20-47-01.png)

Recipe for saving to a hash table:

- Take the key and plug it into the hash function, getting the hash code.
- Modulo that hash code by the length of the underlying array, getting an array index.
- Check if the array at that index is empty, if so, save the value (and the key) there.
- If the array is full at that index continue to the next possible position depending on your collision strategy.

Recipe for retrieving from a hash table:

- Take the key and plug it into the hash function, getting the hash code.
- Modulo that hash code by the length of the underlying array, getting an array index.
- Check if the array at that index has contents, if so, check the key saved there.
- If the key matches the one you're looking for, return the value.
- If the keys don't match, continue to the next position depending on your collision strategy.

```javascript
const LinkedList = require("./LinkedList");
const Node = require("./Node");
class HashMap {
  constructor(size = 0) {
    this.hashmap = new Array(size).fill(null).map(() => new LinkedList());
  }

  hash(key) {
    let hashCode = 0;
    for (let i = 0; i < key.length; i++) {
      hashCode += hashCode + key.charCodeAt(i);
    }
    return hashCode % this.hashmap.length;
  }

  assign(key, value) {
    const arrayIndex = this.hash(key);
    const linkedList = this.hashmap[arrayIndex];
    console.log(`Storing ${value} at index ${arrayIndex}`);
    if (linkedList.head === null) {
      linkedList.addToHead({ key, value });
      return;
    }
    let current = linkedList.head;
    while (current) {
      if (current.data.key === key) {
        current.data = { key, value };
      }
      if (!current.next) {
        current.next = new Node({ key, value });
        break;
      }
      current = current.next;
    }
  }

  retrieve(key) {
    const arrayIndex = this.hash(key);
    let current = this.hashmap[arrayIndex].head;
    while (current) {
      if (current.data.key === key) {
        console.log(
          `\nRetrieving ${current.data.value} from index ${arrayIndex}`
        );
        return current.data.value;
      }
      current = current.next;
    }
    return null;
  }
}

module.exports = HashMap;
```
