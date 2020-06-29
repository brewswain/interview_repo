# Simplifying Big O Expressions

Let's talk about simplifying Big O expressions.

As we remember, we talked about how counting all of the individual operations can be tricky, and that it in fact doesn't really matter that we have every single operation counted out.

All we really care about is the general trend eg. O(n)

Let's discuss some actual rules to help us when simplifying these expressions. To that end, there are some helpful rules of thumb that we can follow:

- Constants Don't matter [O(2n) = O(n), O(500) = O(1), O(13n<sup>2</sup>) = O(n<sup>2</sup>) etc]
- Smaller Terms don't matter [ O(n + 10) = O(n), O(1000n + 50) = O(n) etc]. This also extends to something like O(n<sup>2</sup> + 5n + 8), as it'll simply be simplified as O(n<sup>2</sup>)
  
 ### Big O Shorthands

 Analyzing complexity with big O can get complicated. There are several rules of thumb that can help. Please note that these rules won't always work, but they're a useful starting point:

 - Arithmetic operations are constant.
 - Variable assignment is constant.
 - Accessing elements in an array(by index) or object(by key) is constant.
 - In a loop, the complexity is the length of the loop times the complexity of whatever happens _inside_ the loop.


### Some examples

```
function logAtLeast5(n) {
    for (let i = 1; i <= Math.max(5, n); i++) {
        console.log(i)
    }
}
```

As we can see, we have a loop. This loop will either go from 1 - 5 OR 1 - _n_, whichever one is larger. In this case, all we really care about is what happens as _n_ grows larger since 5 is small. Let's simplify this and say that this Big O is:
- O(n)

```
function logAtMost5(n) {
    for (let i = 1; i <= Math.min(5, n); i++) {
        console.log(i)
    }
}
```

In this case, _n_ growing doesn't matter, as once it exceeds 5, the loop is only going to run 5 times. This means that the Big O is:
- O(1)

