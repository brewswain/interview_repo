# Concrete Examples

Coming up with examples can help you understand the problem better. Examples also provide sanity checks that your eventual solution works how it should via cross-checking.

This also applies on a larger scale, like User stories, or user tests.

### Explore Examples

- Start with simple examples
- Progress to more complex examples
- Explore examples with empty inputs
- Explore examples with invalid inputs

Let's use an example problem to show this workflow:

- #### Write a function that takes in a string and returns counts of each character in the string.

After restating the problem etc to ensure I understand it, it's time to come up with some simple examples:

```
charCount("aaaa"); // {a:4}
charCount("hello"); // {h:1, e:1, l:2, 0:1}
```
That shows what we think the function should output. However, this also brings some more questions to mind. What do we do with the characters that aren't used? Do we output those as well:

```
charCount("aaaa"); // {a:4, b:0, c:0}
```
This is actualy useful, since that would make our life easier since we can pre-define these values as 0, and just increment them as needed.

---

Let's now progress to more complex examples:

```
charCount("my phone number is 867-5309");
charCount("Hello hi");
```

Well, now we have more questions about functionality! Do we want to return spaces? what about special characters and numbers? Do we ignore casing or do we have case-specific output?

---

Now let's look at an empty input:

```
charCount("");
```
What do we want to return when it's called with an empty string? and empty object? maybe `undefined` or something of the like?

---

Finally, let's look at invalid inputs:

```
charCount(34534534)
```
Understanding edge cases in an interview setting often isn't _that_ important, but it's definitely useful in the real world application. This leads to us coming up with a more robust solution.

