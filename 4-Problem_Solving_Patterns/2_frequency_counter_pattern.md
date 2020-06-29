# Frequency Counter 

This first pattern isn't *officially* called frequency counter, but that's the name we'll be using, since the idea behind it is that we use an object to collect a bunch of values and their frequencies.

This therefore makes this pattern useful for when you have multiple pieces of data/inputs and you need to compare them to see if they consist of similar values, are anagrams, etc.

What makes this a good approach is that it's usually O(n), whereas the easier solution is usually nested loops, which would give us O(n<sup>2</sup>) time.

Let's look at an example to clarify this:

- #### Write a function called **same**, which accepts two arrays. The function should return true if every value in the array has its corresponding value squared in the second array. The frequency of values must be the same.

As an example:

same([1,2,3], [4,1,9]) //true
same([1,2,3], [1,9]) //false
same([1,2,1], [4,4,1]) //false (must be the same frequency)

First let's use a 'naive' solution--a suboptimal solution:

```
function same(arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false;
  }
  for (let i = 0; i < arr1.length; i++) {
    let correctIndex = arr2.indexOf(arr1[i] ** 2);
    if (correctIndex === -1) {
      return false;
    }
    arr2.splice(correctIndex, 1);
  }
  return true;
}

```

in this case, we're using nested loops, which means that we have a time complexity of O(n<sup>2</sup>). Please note that even though we only have one for loop, we're using indexOf() which also loops. The splice ensures that we get the correct frequency of values. Again, everything works, but we want to get a better time complexity.

This is where the frequency counter comes into play:

```
function same(arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false;
  }
  let frequencyCounter1 = {};
  let frequencyCounter2 = {};
  for (let val of arr1) {
    frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1;
  }
  for (let val of arr2) {
    frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1;
  }
  for (let key in frequencyCounter1) {
    if (!(key ** 2 in frequencyCounter2)) {
      return false;
    }
    if (frequencyCounter2[key ** 2] !== frequencyCounter1[key]) {
      return false;
    }
  }
  return true;
}
```

Instead of looping over the first array and then checking for each value in a sub-loop over the second array, we can loop over each array one time individually. Remember that two separate loops are vastly better than two nested loops. This approach is a much better time complexity of O(n).

The concept here is that we create two objects. Each one is going to count the frequency of individual values in arrays. Each object will get a key of the array's value, then the object's value will be the frequency that they occur. For clarity, see this example:

```
same([1,2,3,2], [9,1,4,4])

frequencyCounter1 = {1: 1, 2: 2, 3: 1}
frequencyCounter2 = {1: 1, 4: 2, 9: 1}
```

Pretty sweet! The magic part is that we make one more loop. We loop over either frequencyCounter(in our case we did it over the first one), and it looks at how many times each key occurs, and looks for its squared equivalent in the other frequencyCounter. It's a little weird, but actually isn't as confusing as it looks.









