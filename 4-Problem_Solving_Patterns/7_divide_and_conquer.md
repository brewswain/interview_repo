# Divide and Conquer

This pattern is actually documented, so you can google this one up. 

That being said, this set of notes will be structured differently from our previous patterns in this section. We're not going to show **a lot** of code this time, since we're going to tackle a lot of divide and conquer algorithms further on, with different applications, some more complex than others; There isn't one standardized approach here.

We'll see this with sorting algorithms, for example, quick sort and merge sort. Also, we'll show this again in stuff like binary search patterns. Therefore it makes more sense to describe the general idea of divide and conquer here, and then show more targeted applications of this pattern to accomplish different needs later.

So what we do is take a large set of data, such as an array, string, tree, et cetera. Instead of searching from the left to the right, We actually divide our data set into smaller pieces, then do something with each of the smaller pieces of data to decide where we go next. Depending on the problem, this pattern can tremendously decrease time complexity.

A very classic example of this would be using binary search:

- #### Given a sorted array of integers, write a function called search that accepts a value and returns the index where the value passed to the function is located. If the value isn't found, return -1.

```
search([1,2,3,4,5,6], 4)  // 3
search([1,2,3,4,5,6], 6)  // 5
search([1,2,3,4,5,6], 11) // -1
```

The naive approach would be to start from the left, and check each value until we either find our wanted result or return -1:

```
function search(arr, val) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === val) {
      return i;
    }
  }
  return -1;
}
```

- Time Complexity = O(n)

Pretty simple, this approach is called  linear search. Binary search involves a very different approach:

```
function search(arr, val) {
  let min = 0;
  let max = arr.length - 1;

  while (min <= max) {
    let middle = Math.floor((min + max) / 2);
    let currentElement = arr[middle];

    if (currentElement < val) {
      min = middle + 1;
    } else if (currentElement > val) {
      max = middle - 1;
    } else {
      return middle;
    }
  }
  return -1;
}
```
- Time Complexity = Log(n)

While this approach _looks_ a bit verbose, it's actually super simple! This also shows why it's necessary for us to use a sorted array, as we're judging the middle value based on if it's greater than or lesser than `val`. If `val` is less than our middle value, then that means that we simply don't care about any values larger than our middle value! we just split our array that we care about in half, and start looping while looking for our value. 

We then look at our sub array, and repeat the same process (look at the middle array, then get rid of the half of the array that we don't care about by changing our `min` OR our `max`). We repeat this until we either find our `val` or our loop ends without finding it, where we return -1.

We won't go any deeper than this just yet, but keep in mind what a powerful solution this can be!