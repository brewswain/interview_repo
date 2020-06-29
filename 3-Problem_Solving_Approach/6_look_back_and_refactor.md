# Look Back and Refactor

Once we have a solution, it's time to look back and refactor. It's tempting to just end our problem with something that just works. However, looking at the code and figuring out what you don't like about the code's efficiency/legibility is really important.

Some good questions to ask are as follows, sometimes out loud:

- Can you check the result?
- Can you derive the result differently?
- Can you understand it at a glance?
- Can you use the result or method for some other problem?
- Can you improve the performance of your solution?
- Can you think of other ways to refactor?
- How have other people solved this problem?

Let's go through our good friend, charCount():

```
function charCount(str) {
  let result = {};
  for (let i = 0; i < str.length; i++) {
    let char = str[i].toLowerCase();
    if (/[a-z0-9]/.test(char)) {
      if (result[char] > 0) {
        result[char]++;
      } else {
        result[char] = 1;
      }
    }
  }
  return result;
}
```
As you can see, we added a new if statement that uses regular expressions to check to see if the characters are alphanumeric. Then we do the same logic we've done beforehand. This solution works!

However, let's look at what we can improve/refactor. First of all, let's replace our for loop with a `for of` loop, as if we do `for of` on a string it'll give us each character immediately:

```
function charCount(str) {
  let result = {};
  for (let char of str) {
    let char = char.toLowerCase();
    if (/[a-z0-9]/.test(char)) {
      if (result[char] > 0) {
        result[char]++;
      } else {
        result[char] = 1;
      }
    }
  }
  return result;
}
```

Now that we've done that, let's make some syntax changes for our conditional statement:

```
function charCount(str) {
  let result = {};
  for (let char of str) {
    let char = char.toLowerCase();
    if (/[a-z0-9]/.test(char)) {
      result[char] = ++obj[char] || 1;
    }
  }
  return result;
}
```

Much neater! Ternary operators are pretty freaking sweet. Lastly, let's make our most important change though. We used regex here because it's simple, but we're not sure how efficient it really is. Regex's performance can vary based on browser, etc, so let's see if we can decide on a more performant approach.

We  can replace our regular expression with a charCodeAt() numerical representative of our character, then check to see if our character code is within range. It's more verbose, but offers better performance, so gj us!

Of course, this approach relies a lot on having that preset knowledge of our character codes which most people don't have off hand, but it's still useful to show how many different approaches we can make.

Just for reference, the code would look something like this:

```
function isAlphaNumeric(char) {
    let code = char.charCodeAt(0);
    if (!(code > 47 && code < 58) &&  // numeric (0-9)
        !(code > 64 && code < 91) &&  // upper alpha (A-Z)
        !(code > 96 && code < 123)) { // lower alpha
            return false;
        }
        return true;
}
```

We would then refactor our charCount() to work with our helper function:

```
function charCount(str) {
  let result = {};
  for (let char of str) {
    let char = char.toLowerCase();
    if (isAlphaNumeric(char)) {
      result[char] = ++obj[char] || 1;
    }
  }
  return result;
}

function isAlphaNumeric(char) {
    let code = char.charCodeAt(0);
    if (!(code > 47 && code < 58) &&  // numeric (0-9)
        !(code > 64 && code < 91) &&  // upper alpha (A-Z)
        !(code > 96 && code < 123)) { // lower alpha
            return false;
        }
        return true;
}
```

As we can see, our solution looks incredibly different from our initial one. This is really useful and important to grasp, so keep this in mind.






