# Space Complexity

So far, everything that we've been worrying about has been with reference to time; how fast the algorithm runs. That's called time complexity. Now let's talk about the space that the algorithm takes up as the size of the input increases.

We can still use Big O notation to analyze space complexity--i.e. the amount of additional memory we need to allocate in order to run the code in our algorithm.

You may hear the term auxiliary space complexity sometimes. This refers to space required by the algorithm itself, not including space taken up by the inputs. This is what we care about, as we're strictly worried about the performance of the algorithm. Unless directly noted, whenever we talk about space complexity, we're technically actually talking about auxiliary space complexity.

### Rules of Thumb

- Most primitives (booleans, numbers, undefined, etc) are constant space
- Strings require O(n) space (where _n_ is the string length)
- Reference types are generally O(n) where _n_ is the length(for arrays) or the number of keys(for objects)

As an example, please see below:

```
function sum(arr) {
    let total = 0;
    for (let i = 0; i < arr.length; i++) {
        total += arr[i];
    }
    return total;
}
```

Keep in mind that we're focusing on space complexity here. 

This function takes an array and sums all of the items in said array. No matter what array length, we have one variable called total. Inside the for loop, we have a single declaration(let i = 0). That's it for space!

We're adding into our `total` variable, but that doesn't matter. That takes time, but the space is already there. No matter the size of our array, it has no impact on the space that our algorithm takes up, since we only have 2 variables, and they exist no matter what. This all means that we have constant space, which therefore means in Big O that we're O(1)!

Let's look at another example:

```
function double(arr) {
    let newArr = [];
    for (let i = 0; i < arr.length; i++) {
        newArr.push(2 * arr[i]);
    }
    return newArr;
}
```

This function takes an array, and it doubles the value of each item inside of our array that we pass in, aka double([1, 2, 3]) would return us [2, 4, 6]. What's important to note here is that it makes a new array, which it then loops to push our new values over into.

For space complexity, we make a new array, which is again one variable, and our single declaration of (let i = 0). However, inside of our loop, we're actually pushing to our newArray, which means that it's getting longer and longer with each iteration directly in proportion with the length of the input. For instance, if our input array has 50 items, we'll be increasing the length of our newArray by 50 items.

This therefore means that the space we're taking up is directly proportional to the input, _n_, which means that once we simplify it from O(n + 2), we have O(n) space. 