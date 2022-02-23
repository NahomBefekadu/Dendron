
Recursion is useful for many other data structures and computer programs. One of the best examples of recursion is the fibonacci sequence.

```javascript
let fibonacci = function (f) {
  if (f < 0) {
    console.log("index error");
  } else if (f == 0) {
    return 0;
  } else if (f == 1) {
    return 1;
  }
  let fn = [0, 1];
  for (let i = 2; i < f + 1; i++) {
    fn.push(fn[i - 1] + fn[i - 2]);
  }
  return fn[f];
};

let j = fibonacci(9);
console.log(j);
//34
```

To see how the call stacks work lets take a look at calling the function fibonacci(4).

This would result in the function being called nine times, as it recursively calls the function each time as shown below.

```terminal
F(4) - F(3)  - F(2) - F(1)
       F(3)  - F(2) - F(1)
               F(2) - F(1)
```
