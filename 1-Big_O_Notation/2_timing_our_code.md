# Timing Our Code

As an example, let's suppose that we want to write a function that calculates the sum of all numbers from 1 up to (and including) some number _n_.

eg: myFunction(3) should equal 1+2+3.

The most common solution would be something like this:

```
function addUpTo(n) {
    let total = 0;
    for (let i = 1; i <= n; i++) {
        total += i;
    }
    return total;
}
```

Basically we create an accumulator (In this case `total`), add each number 1 at a time to `total`, up until i becomes > n at which point the loop'll stop. Pretty simple and neat!

Let's look at a second solution:

```
function addUpTo(n) {
    return n * (n + 1) / 2;
}
```

This solution is a lot shorter (that doesn't inherently make it better, but it's still a factor). It's also less intuitive though. No loop, we're just using a mathematical formula, and it also works.

Which one is better?

## What does better actually mean?

- Faster?
- Less memory-intensive?
- More readable?

All of these concerns are valid, but have different weight depending on the problem that this solution is looking to solve (The first 2 are often more heavily focused on for obvious reasons, but this often comes at the expense of readability). For now let's focus on Speed.

---

### Speed

When it comes to evaluating speed, the simplest way is to use something like a timing function:

```
function addUpTo(n) {
    let total = 0;
    for (let i = 1; i <= n; i++) {
        total += i;
    }
    return total;
}

let t1 = performance.now(); // built-in performance tracking method
addUpTo(1000000000);
let t2 = performance.now();
console.log(`Time Elapsed: ${(t2 - t1) / 1000} seconds.`)
```

The above should log us the amount of time that elapsed between `t2` and `t1`. For reference, we get around 1.25 seconds.

An interesting thing to note here is that if we ran this code multiple times, we would get a varied time returned to us.

Let's do the exact same thing for our other option we did:

```
function addUpTo(n) {
    return n * (n + 1) / 2;
}

let t1 = performance.now(); // built-in performance tracking method
addUpTo(1000000000);
let t2 = performance.now();
console.log(`Time Elapsed: ${(t2 - t1) / 1000} seconds.`)
```

The above shows that we get a way smaller number (something around 0.0001 seconds). That's a pretty huge difference! It shows that our second method is way more efficient.

However, this process **isn't** particularly reliable. Manually timing stuff before and after doesn't give us the most quantifiable results. How would we actually label this?

---

### The Problem with Time

- Different machines will record different times.
- The _same_ machine will record different times(as we mentioned).
- For fast algorithms, speed measurements may not be fast enough.

Timing our code is definitely still useful, but it would definitely bring us more value if we had an alternate method of measuring, wouldn't it? (foreshadowing alert, look at the next file for our solution to this problem)
