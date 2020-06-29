# Counting Operations

If we're not going to use time, then what should we do?

Well, rather than counting the seconds that the code takes to run, we can count the _number of simple operations_ the computer has to perform!

Let's look at the faster solution we used in our last file:

```
function addUpTo(n) {
    return n * (n + 1) / 2;
}
```

From left to right, we can see that we have 1 multiplication, 1 addition, and 1 division. So we have 3 operations, but what about the values? Actually, this doesn't matter much in this case. No matter the value, the amount of operations we have to do is still a simple 3!

Let's look at our other solution:

```
function addUpTo(n) {
    let total = 0;
    for (let i = 1; i <= n; i++) {
        total += i;
    }
    return total;
}
```

This one has a few more operations. This may seem silly, as we only have 1 physically written operation here, which is `total += i`, but you need to remember that this is inside a loop.

If the loop were to run 5 times, then that means that there are 5 operations taking place, etc. This means that instead of simply saying that we have a set amount of operations, we say that this approach has _n_ operations.

But we're not done here, because we actual have _n_ assignments too! Remember that our iterator is `total += i`, not `total + i`.

That being said, we don't need to have a completely accurate counting of the minutiae of our additions/assignments, as all that matters is a general overview. This also means that the conditions of our loop itself are also the victim of additions and assignments as needed:

- total = 0 (1 assignment)
- i = 1 (1 assignment)
- i <= n (_n_ comparisons)
- i++ (_n_ additions and assignments)

This is a lot, which means that counting these operations can be tricky. How do we generalize it? Well, there are calculations we can run (In this case, something like 5*n* + 2 should work out if we ran the operation 5 times [2 for the calculations that aren't gonna be looped]).

That being said, regardless of the exact number, the number of operations grows roughly proportionally with _n_.
