# Multiple Pointers countUnique Values Challenge

Let's look at a problem that'll utilize multiple pointers, but this time, it'll require the points start on the same side of the array:

- #### Implement a function called countUniqueValues, which accepts a sorted array and counters the unique values in the array. There can be negative numbers in the array, but it will always be sorted.

```
function countUniqueValues(arr) {
  let left = 0;
  let right = 1;
  let uniqueValues = 0;

  if (arr.length > 0) {
    uniqueValues = 1;
  }
  while (right < arr.length) {
    if (arr[left] !== arr[right]) {
      left = right;
      uniqueValues++;
    }
    if (arr[left] === arr[right]) {
      right++;
    }
  }
  return uniqueValues;
}
```

- Time Complexity = O(n)
- Space complexity = O(1)

This shows my approach. We initially set our left and right indices for our array and our `uniqueValues` as 0. This ensures that if we input an empty array as our method's parameters, it would return 0. Then, we put a simple if statement that detects if the array is empty or not. If it isn't empty, we give it 1 unique value by default. From there, we supply a while loop that runs while `right` is less than our array's length. Inside the loop, we have some conditions where if our `left` position has a different value from our `right` position, we simply it over to our `right`, and then increase our `uniqueValues` by 1. Then, any time that our `left` and `right` positions are equal, we move our `right` one more position closer to the end of the array. when the loop is complete, we return our `uniqueValues`.

It works pretty well!
Let's look at the alternate approach that definitely looks a bit neater:

```
function countUniqueValues(arr) {
  if (arr.length === 0) return 0;
  let left = 0;
  for (let right = 1; right < arr.length; right++) {
    if (arr[left] !== arr[right]) {
      left++;
      arr[left] = arr[right];
    }
  }
  return left + 1;
}

```

- Time Complexity = O(n)
- Space complexity = O(1)

Nice, this is a very neat solution! as we can see, our for loop takes care of `right` incrementing so we don't need to worry about a default condition to make it move, which leaves us with our rather interesting solution. You may have noticed that while our original solution set `left` = `right`, this solution actually sets our arr[left] to = arr[right] after shifting `left` to the right once.

This is nice because if we had, for instance, an array like this:

[1,1,1,1,1,1,3,4,5]

then once we ran our program, our loop would end up with:

[1,3,4,5,1,1,3,4,5]

Now, this _looks_ a bit confusing to us, but it's fine because now all we do is return `left` + 1(remember that `left` started at 0 so it would always be one number behind) and that'll actually equal the unique values we have!
