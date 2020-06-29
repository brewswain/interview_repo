# Big O of Objects

Objects are unordered data structures, where everything is stored in key-value pairs:

```
let instructor = {
    firstName: "Kelly",
    isInstructor: true,
    favoriteNumbers: [1,2,3,4]
}
```

###  When to use objects

- When you don't need order
- When you need fast access/insertion and removal

For reference, when we say fast, here's the big O of object interactions:

- Insertion - O(1)
- Removal - O(1)
- Access - O(1)
- Searching - O(n)

As shown above, objects are extremely fast, getting constant time for access/insertion/removal. 

However, searching is linear time - O(n). Please note that when we say "searching" , we don't mean looking for a key, like `firstName`. As we've already seen, accessing info with a key is constant time. AWhat we're talking about is checking to see if a given piece of information is in a **value** somewhere. 

Basically, if we were looking for `true`, we would look through every single one of our keys till we found it. This means that as the number of properties grow(_n_), so does the amount of time it takes to do them.

### Big O of Object Methods

- Object.keys - O(n)
- Object.values - O(n)
- Object.entries - O(n)
- hasOwnProperty - O(1)





