# Logarithms

Be warned, here lieth the math.

We don't need to me masters of logarithms or anything here, but we do need a basic understanding of them as some algorithms that we'll see will have a big O that isn't as simple as the ones we've gone over, aka O(1), O(n), O(n<sup>2</sup>). These complexities _are_ very common, but sometimes there are big O expression that involve more complex mathematical expressions.

### What _is_ a Logarithm?

A logarithm is the inverse of [exponentiation](https://en.wikipedia.org/wiki/Exponentiation).
For instance, we might see this:


- log<sub>2</sub>(8) = 3

What this really is asking is:

To what power does 2 equal 8? 

We know that 8 is the equivalent of 2<sup>3</sup>, so therefore, the log<sub>2</sub> of 8 is 3. in a formulaic way, we can say therefore that:

- log<sub>2</sub>(8) = 3   ------>   2<sup>3</sup> = 8
- log<sub>2</sub>(value) = exponent   ------>   2<sup>exponent</sup> = value

Logarithms aren't always working with <sub>2</sub>, but it's pretty common so keep that in mind. With this in mind, in order to help us with further simplification for Big O notation in particular we'll omit the <sub>2</sub>:

- log === log<sub>2</sub>


### Logarithm Complexity

Logarithmic time complexity is great! If we have an algorithm with O(log n), that's fantastic.

Certain Searching algorithms have logarithmic time complexity, which we'll see as we go further into this course. Also, efficient sorting algorithms often involve logarithms. Recursion also sometimes involves logarithmic space complexity.


