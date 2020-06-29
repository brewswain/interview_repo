# Solve or Simplify

Sometimes, once you've done all the prior steps, you might be able to solve the problem. However, sometimes you just can't reach that step as yet. This is where we try to simplify it!

By solving a simpler problem, we mean to try to ignore the part of the problem that's giving us a hard time to focus on fixing everything else. 

Let's discuss the steps for simplification:

- Find the core difficulty in what you're trying to do
- Temporarily ignore that difficulty
- Write a simplified solution
- Incorporate that difficulty back in

Let's use our good ol' example to help us out:

- #### Write a function that takes in a string and returns counts of each character in the string.

Assuming that determining that a character is alphanumeric gives us trouble, let's start by creating an object and figuring out our loop:


```
function charCount(str){
    // Make object to return at end
    let result = {};
    // loop over string, for each character
    for (let i = 0; i < str.length; i++) {
        let char = str[i].toLowerCase();
        // If the character is a number/letter and key in object, add one to count
        if(result[char] > 0) {
            result[char]++
        } else {            
        // if the character is not in object, ad it and set value to 1.
            result[char] = 1;
        }
    }

        // if character is something else (space, period, etc.) don't do anything
    // return object at end
    return result;
}
```

So far this prints out our solution, but we haven't figured our alphanumeric problem. However, now we show that we understood the main functionality of our problem, and now we can do some additional research, maybe even secure a hint from our interviewer.
Assuming we figured it out, we can now add it to our solution. We'll go over the actual solution in the next file, but this shows how simplifying this approach allows us to actually put code into our problem and demonstrates our problem-solving ability.


