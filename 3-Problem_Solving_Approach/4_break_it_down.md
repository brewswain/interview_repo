# Break it Down

Before we start writing code, let's break the problem down by taking the steps of the problem and write it down. Explicitly write out the steps you need to take. 

This forces you to think about the code you'll write before you write it, and help you catch any conceptual issues or misunderstandings you have before you dive in and worry about details like syntax etc.

Let's look at an example breakdown:

- #### Write a function that takes in a string and returns counts of each character in the string.

```
// put some expected output as shown in last file

function charCount(str) {
    // Do something
    // Return an object with keys that are lowercase alphanumeric characters in the string.
    // Values should be counts for those characters
}

function charCount(str) {
    // Make object to return at end
    // loop over string, for each character
        // If the character is a number/letter and key in object, add one to count
        // if the character is not in object, ad it and set value to 1.
        // if character is something else (space, period, etc.) don't do anything
    // return object at end
}
```




