# The Call Stack

Before we start talking about writing our own recursive functions, let's talk about what happens behind the scenes when we call functions in JavaScript.

If a recursive function calls itself over and over, what actually happens?

In almost all program languages, there's a built in data structure that manages what happens when functions are invoked. This data structure is known as a **Call stack**.

As the name suggests, it's a stack data structure. We'll discuss stacks later on but just keep that in mind. Any time a function is called, it's placed on the top of the call stack(push). Whenever JavaScript sees the `return` keyword or the function ends, the compiler will remove it (pop). This ensures that we call our functions synchronously. This also means that when we call a function from _inside_ of another function, it'll operate on the recently called function before completing the original function.

I said function way too many times, but let's look at some simple code:

```
function firstFunction() {
    console.log("hello, let's call our second function.")
    secondFunction()
    console.log("ok we're all done now!")
}

function secondFunction() {
    console.log("Hey, I'm the second function.")
}
```

If we were to console.log our firstFunction(), our output would therefore be:

```
hello, let's call our second function.
Hey, I'm the second function.
ok we're all done now!
```

This is obviously a very simplified example, but this shows that firstFunction() actually got paused to call and complete secondFunction(), _and then_ console.log our "ok we're all done now!" message.

This is how stacks work. Anytime we make a new call, the newest call gets placed at the top of the stack, which we work on. Once our function is done, then it gets removed from the stack, which lets it work on the other functions on stacks.

### This is cool, but what about recursion?

The reason this is important to understand is that whenever we write recursive functions, we actually keep pushing new functions onto the call stack! We'll go a bit more into this in the next file when we actually create our own recursive function.
