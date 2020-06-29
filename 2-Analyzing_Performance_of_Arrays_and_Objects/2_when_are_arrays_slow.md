# When are Arrays slow

The big selling point of arrays is that they're ordered, unlike objects. That's often useful whenever we need order, but it comes at a performance cost when we need insertion and removal.

### Big O of Arrays

- Insertion - It depends
- Removal - It depends
- Searching - O(n)
- Access - O(1)

A misconception about arrays is that whenever we access an array element, javascript isn't going through every element until it finds that one specified element. It doesn't matter how long an array is, it's constant time.

However, let's look at insertion and removal.

If we want to add an element to the end of an array, it's O(1) as there aren't any complexities of what we're trying to accomplish. **However**, a problem arises when we try to insert at the beginning of the array. This is because by doing this, we shift the indices of every element in said array. This means that we'll need to re-index every element in our array. Therefore, inserting at the beginning of the array is O(n). The same goes for removing an element at the beginning of an array.

This means that push() and pop() are always faster than shift() and unshift() unless it's an empty array.




