# Sliding Window

The next pattern we'll talk about is called the sliding window. This approach is useful when we have a set of data like a string or an array, and we're looking for a subset of that data that is continuous in some way. Let's look at an example:

```
"hellothere"
```

Let's say that we were asked to write a function to find the longest sequence of unique characters. In this case, we'll have two potential answers; "hel" and "lother". In this case, our answer would be  "lother".

An additional example of what we might use this pattern for is as follows:

- #### Write a function called maxSubarraySum which accepts an array of integers and a number called _n_. The function should calculate the maximum sum of _n_ consecutive elements in the array.

```
maxSubarraySum([1,2,5,2,8,1,5], 2) // 10
maxSubarraySum([1,2,5,2,8,1,5], 4) // 17
maxSubarraySum([4,2,1,6],1)        // 6
maxSubarraySum([],4)               // null
```

So as seen from the example output data above, _n_ represents how many numbers we're going to add together from our array to see what the highest value we get is. That means the first function call can add 2 **consecutive** numbers together, the second call can add 4, etc.

How we do is is to make a **window**, which can be a single variable, subarray, or even a string. We move that window depending on a condition. We slide it up usually from left to right, but you can do it from right to left too or start in the middle.

It's useful in these problems where we're keeping an eye on a subset of data in a larger pool of data. Let's look at actually solving this problem. If we look at our question, this shows that the array doesn't have to be sorted, it's just integers in an array.

As always, let's start with the naive version of this implementation. We'd probably start with a loop and then have a nested loop that looks ahead and sums _n_ variables, and then move forward one space, and compare sums, while keeping track of the larger sum.  We'd then do that until we've looped through the array, and keep the largest version. Let's look at how that'll look in code:

```
function maxSubarraySum(arr, num) {
  if (num > arr.length) {
    return null;
  }
  let max = -Infinity;
  for (let i = 0; i < arr.length - num + 1; i++) {
    temp = 0;
    for (let j = 0; j < num; j++) {
      temp += arr[i + j];
    }
    if (temp > max) {
      max = temp;
    }
  }
  return max;
}
```

- Time Complexity = O(n<sup>2</sup>)

We begin by ensuring that we'd return `null` for any edge cases involving not enough elements to sum.

We then declared our max value at negative infinity to cover for the possibility of an array of all negative numbers. Of course, this means that if we were working with only positive sums, then we could start at 0.

Now for the weird double loop that we've done. Our first loop goes until we're almost at the end of the array. This is because we don't want to go to the last value and try to add multiple digits together; we want to stop where the final number being added for our sum is at the end of the array.

...That was kind of confusing, let me show you what I mean:

```
maxSubarraySum([1,2,5,2,8,1,5], 4)
```

Instead of us wanting our loop to finish at the last element in our array, which in this case is `5`, we'd want to end at the second `2`, which in this case would sum this:

```
2 + 8 + 1 + 5 
```

Remember that we're adding from left to right, so this is the perfect spot to end. Therefore, this means that we'll want to end our sum _n_ - 1 spaces from the array's final element so that we can sum _n_ numbers. Pretty neat! This also means that if _n_ was 1, we'd end at the last element.

So that's what our ` i < arr.length - num + 1;` does. Look at our array of [1,2,5,2,8,1,5], then subtract  our array's length from our _n_, then add 1, and see where we're positioned!

So now that we've established that our first loop simply navigates to each spot in our array to ensure that we can correctly sum our array values, let's look at our nested loop _after_ making a variable called `temp` that'll start at 0.

We use `temp` to store our sum each time through. Our second loop
Then adds our values of arr[i] with arr[j] and places the sum's result in `temp`, where arr[j] shifts every iteration of the loop until j reaches our value of _n_. This ensures that we only add _n_ numbers together. 

If `temp` is then > `max`, `max` then gets its value replaced with `temp`. I know this is a bit verbose, but this is pretty much how it works, and has some interesting ideas so I wanted to go a little in depth here.

Now let's talk about this method's downfalls. Again, time complexity isn't good because of our nested for loops. So let's look at a more efficient solution:

```
function maxSubarraySum(arr, num) {
  let maxSum = 0;
  let tempSum = 0;
  if (arr.length < num) return null;
  for (let i = 0; i < num; i++) {
    maxSum += arr[i];
  }
  tempSum = maxSum;
  for (let i = num; i < arr.length; i++) {
    tempSum = tempSum - arr[i - num] + arr[i];
    maxSum = Math.max(maxSum, tempSum);
  }
  return maxSum;
}
```

- Time Complexity = O(n)

This solution is instantly more efficient, with a time complexity of O(n). Let's look at how this solution works.

We begin by declaring our `max` and `temp` sum values. In this case, we're assuming that we're only adding positive numbers, so our maxSum starts at 0. 

Our first loop we sum together our first _n_ numbers in a row and place that in our `maxSum`. We then set our `tempSum` to that value, and use it in our next loop, which uses a pretty interesting solution.

Instead of manually adding all 3 numbers again, we simply subtract our first number from our initial range, then add the new number! Let's look at what we mean:

```
[1,2,5,2,8,1,5],3
```
We begin by adding 1 + 2 + 5 = 8.

Then we subtract 1 from our sum, and add 2, which would = 9.

Then we subtract 2 from our sum, and add 8. And so on, and so forth. This is a really clever solution that minimizes the amount of calculations that needs to happen! This is where the _sliding_ part of Sliding Window comes into play. We're simply _sliding_ our calculation, 1 by 1. Pretty freaking sweet!

We then compare our current `tempSum` with our `maxSum` by using Math.max(), which pretty much does the same thing as our `if` statement we used in our previous solution(if (temp > max) max = temp) and return that value.

This means that we'll only loop through our array once, which is much more efficient than our first solution.