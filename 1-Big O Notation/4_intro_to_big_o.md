# Introduction to Big O

Big O is a way to normalize fuzzy counting. It allows us to talk formally about how the runtime of an algorithm grows as the inputs grow.

We don't care about the details, only the broad trends (How _n_ affects our runtime, operations, assignments etc.)

### Big O Definition

We say that an algorithm is O(f(n)) if the number of simple operations the computer has to do is eventually less than a constant times f(n), as _n_ increases.

- f(n) could be linear (f(n) = n)
- f(n) could be quadratic (f(n) = n<sup>2</sup>)
- f(n) could be constant (f(n) = 1)
- f(n) could be something entirely different

f(n) simply means a function with an input of _n_, with what's to the right of our `=` being our output btw

This means, therefore that we're describing the relationship between the input and the runtime. 

It could be linear, meaning that as _n_ scales, the runtime scales as well, which we've already seen. However, it could also be quadratic, where as _n_ grows, the runtime actually squares to the value of _n_ itself (That's pretty tricky). It could also be constant, where as _n_ grows, it doesn't have an input(We've seen this as well with our more efficient solution!). It could also be entirely different, which we'll check out later in this course.

All of this means that when we talk about Big O, we're actually talking about the worst case scenario. We're talking about the upper bound for runtime. 

Returning to our examples, if we were to look at:

```
function addUpTo(n) {
    return n * (n + 1) / 2;
}
```

As we always have 3 operations, we can say that our f(n) is roughly constant (there's always going to have some slight variance in runtime). This means therefore that we have a Big O of 1. The notation looks like:

- O(1)

This tells us that as _n_ grows, our runtime stays constant; the value is always 1.

If we were to look at our other example, however:

```
function addUpTo(n) {
    let total = 0;
    for (let i = 1; i <= n; i++) {
        total += i;
    }
    return total;
}
```

As we've discussed, as _n_ grows in this application, our runtime grows. This means that the number of operations is eventually bounded by a multiple of _n_ (for example, 10 _n_). This means that we have a Big O of _n_:

- O(n)

We're mainly concerned with the order of magnitude, so we're not concerned if it's 10 _n_, 50000 _n_, or 1 _n_, as O(n) tells us that it's linear.

Let's look at a new example:

```
function countUpAndDown(n) {
    console.log("Going up!");
    for (let i =0; i < n; i++) {
        console.log(i);
    }
    console.log("At the top!\nGoing down...");
    for (let j = n - 1; j >= 0; j--) {
        console.log(j)
    }
    console.log("Back down. Bye!")
}
```

Pretty simply, the above will count up till it reaches the number before _n_, then count backwards until the number reaches back to 0, before logging out our final message.

Let's break this down a bit, as we have multiple loops:

```
for (let i =0; i < n; i++) {
    console.log(i);
}
```
Our first for loop, has roughly O(n) operations. As _n_ grows, so too will our runtime. The same thing goes for our second loop:

```
for (let j = n - 1; j >= 0; j--) {
    console.log(j)
}
```    

Our initial thought might be our Big O is 2n: 
- O(2n)

However, as previously discussed, we don't care about the magnitude of _n_ in this case as both are linear, so we actually just write our Big O as:
- O(n)

Let's work on one more example:

```
function printAllPairs(n) {
  for (let i = 0; i <= n; i++) {
    for (let j = 0; j <= n; j++) {
      console.log(i, j);
    }
  }
}
```

This approach is instantly interesting to us, as we have a nested loop. In this case, if we were to call it like printAllPairs(5), it will print us every pair from (0, 0), (0, 1), etc. leading up to (5, 5).

This approach is really interesting, because as we expect, each of these individual loops are O(n). However, since the second loop is nested inside the first, this will actually give us something like:

- O(n * n) which means O(n<sup>2</sup>).

So as _n_ grows larger, our runtime will increase proportionally to _n_ * _n_.