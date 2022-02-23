---
id: Z628Wpyg2J9hUV8Ys6GcY
title: merge-intervals
desc: ""
updated: 1645477361521
created: 1645475107096
---

## Question

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the mutually exclusive intervals in the input.

#### input:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]

#### Output:

Output: [[1,6],[8,10],[15,18]]

## Solution

To solve this problem we first sort our array of intervals, so that we are able to merge the overlapping intervals.

For any given interval there's six ways they relate to each other as shown below:
![](/assets/images/2022-02-21-15-31-32.png)

lets look at [1,3] and [2,6], if we check the start of our second sub array with the end of our first sub array. we see that the start of the second subarray is less. Therefore we can say theres an overlap at this interval.

As our array is sorted the starting element of our first subarray will be the start of the new sub array in our results array. To find the ending of our subarray we set it equal to the max end element of both sub arrays.

```terminal
x.start <= y.end
z.start = x.start
z.end = Math.max(x.end,y.end)
/------------------/
z.start =1;
z.end = Math.max(3,6)=6
z=[1,6]
```

using the format shown we can implement that in our code below. We first sort our array based on the start number of each subarray.

Then we set a start and end value to our first array, and set up a loop to start from our second subarray to implement our check algorithm outlined above.

#### Javascript

```javascript
var merge = function (intervals) {
  merged = [];
  if (intervals.length < 2) {
    return intervals;
  }
  intervals.sort((a, b) => a[0] - b[0]);
  let start = intervals[0][0];
  let end = intervals[0][1];
  for (let i = 1; i < intervals.length; i++) {
    let currentInterval = intervals[i];
    if (currentInterval[0] <= end) {
      end = Math.max(end, currentInterval[1]);
    } else {
      merged.push([start, end]);
      start = intervals[i][0];
      end = intervals[i][1];
    }
  }
  merged.push([start, end]);
  return merged;
};
```

#### Java

```java

```

## Concepts

- [[data-structures.arrays]]

## Patterns

- Merge Intervals
