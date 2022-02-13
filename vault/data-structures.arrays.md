---
id: 0WlW3iokuTpYX6JNGAQAS
title: Arrays
desc: ""
updated: 1644636847186
created: 1641160304997
---

Arrays are the most used data structures, and is a fundemental data structure.

A static array is a fixed length container which contains n elements that is indexable from the range 0 to n-1. Static Arrays are created as continuous chunks of memory, each element in the static array is sequential addressed.

Static arrays are used for storing and accessing sequential data, temporarily store objects, used as buffers in IO, used in dynamic programming to cache subproblem answers and more.

Compared to static arrays, dynamic array can grow and shrink in size. Generally a dynamic array can be created using a static array, we can do so by checking the size of our current array and elements being inserted. Then based on size of our element and array we can double our static array if we find we can't fit our element into our static array. Thus we can keep continuing resizing our array as we add elements to our static array.

In an Array when we access an array due to it being indexable the time is constant at O(1), where as if we're searching for an element it'll be a linear time of O(n) similar to insertion and deletion.

Below are some methods to traverse an array and sort an array.

Javascript

```javascript
const nums = [];
const nums = new Array();
const nums = new Array(5).fill(0);
for (const num of nums) {
  console.log(num);
}
for (let i = 0; i < nums.length; i++) {
  console.log(nums[i]);
}
//sort
nums.sort((a, b) => a - b);
```

---

Java

```java
String [] name = new String [];


for (String name : names) {
  System.out.println(name);
}
for (int i = 0;i<names.length;i++) {
  System.out.println(name);
}
Arrays.stream(names).forEach(System.out::println);
System.out.println(Arrays.toString(names));
System.out.println(Arrays.deepToString(names));
//sort
Arrays.sort()
```
