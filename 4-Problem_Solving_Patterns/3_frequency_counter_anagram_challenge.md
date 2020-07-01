# Frequency Counter Anagram Challenge

Let's look at a new problem that should use the same frequency Counter style solution that we just did. It has to do with writing a function called validAnagram():

- #### Given two strings, write a function to determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another.

My solution is as follows:

```
function validAnagram(str1, str2) {
  if (str1.length !== str2.length) {
    return false;
  }

  let frequencyCounter1 = {};
  let frequencyCounter2 = {};

  for (char of str1) {
    frequencyCounter1[char] = (frequencyCounter1[char] || 0) + 1;
  }
  for (char of str2) {
    frequencyCounter2[char] = (frequencyCounter2[char] || 0) + 1;
  }

  for (matchedChar in frequencyCounter1) {
    if (frequencyCounter1[matchedChar] !== frequencyCounter2[matchedChar]) {
      return false;
    }
  }

  return true;
}
```
