# Multiple Pointers

Again, this isn't the official name for this pattern, but the idea is that we create pointers or values that correspond to an index or position, and move towards the beginning, end, or middle based on a certain condition. It's very efficient for solving problems with minimal space complexity as well.

The idea is that we have some sort of linear structure like an array, string, linked list etc, and we're going to be searching for (usually) a pair of items that meets some criteria. We use two references, and move as needed. for example, if we have an array:

[-4,-3,-2,-1,0,1,2,3,4]

We might set our first position as -4, our second position as 4, and move towards the middle value of our array (which in this case would be 0).

Keep in mind that the direction of this search is not guaranteed. This also comes up pretty often, so definitely keep this in mind.

Let's use this in an example problem:

- #### Write a function called sumZero which accepts a _sorted_ array of integers. The function should find the first pair where the sum is 0. Return an array that includes both values that sum to 0, or undefined if a pair does not exist.

Before we show the solution, note that this only works in a _sorted_ array.

Anyway, let's look at the naive solution first:

```
function sumZero(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] + arr[j] === 0) {
        return [arr[i], arr[j]];
      }
    }
  }
}
```

- Time Complexity = O(n<sup>2</sup>)
- Space Complexity = O(1)

As you can see, we're using nested for loops. How this works is that our first loop starts a pointer looking at the first array's value. Let's use an example array to show this:

[-3,-2,-1,0,1,2,3]

So our first loop looks at -3. Our second loop then looks that the next index in the array, and adds our first pointer(i) to our second pointer(j). If these pointers sum to 0, then we return the values of each pointer. If it doesn't sum to 0, then j moves down one more position and repeats the process. If the loop completes without anything summing to 0, our first loop will shift our first pointer's index from -3 to -2. Our second loop repeats the process etc. If we have no matching values, then we'll get returned `undefined`.

For visualization of how this works, please see below:

```
sumZero([-3, -2, -1, 0, 1, 2, 3])
-3 + -2 = -5
-3 + -1 = -4
-3 + 0 = -3
-3 + 1 = -2
-3 + 2 = -1
-3 + 3 = 0

return [-3, 3]
```

```
sumZero([-4, -2, -1, 0, 1, 2, 3])

-4 + -2 = -6
-4 + -1 = -5
-4 + 0 = -4
-4 + 1 = -3
-4 + 2 = -2
-4 + 3 = -1

// No matching values, moves marker once

-2 + -1 = -3
-2 + 0 = -2
-2 + 1 = -1
-2 + -2 = 0

return [-2, 2]
```

Obviously, this is a **lot** of iteration. So even though it works, let's use the multiple pointers pattern:

```
function sumZero(arr) {
  let left = 0;
  let right = arr.length - 1;
  while (left < right) {
    let sum = arr[left] + arr[right];
    if (sum === 0) {
      return [arr[left], arr[right]];
    } else if (sum > 0) {
      right--;
    } else {
      left++;
    }
  }
}
```

- Time Complexity = O(n)
- Space Complexity = O(1)

This approach is instantly way more performant. As we can see, we have two pointers, `left` and `right`. `left` starts at the front of the array, while `right` starts at the end. We use a while loop to ensure that while our `left` value is less than our `right`, we sum them, with the iteration's conditions being that if the sum is greater than 0, aka if the `right`'s value is too high, then we shift the right down. Conversely, if our sum is less than 0, that suggests that the `left`'s value is too negative to continue, so we shift `left`'s position once to the right.

Of course, this approach heavily depends on the input being sorted, for obvious reasons, so keep that in mind.
