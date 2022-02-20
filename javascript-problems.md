# Questions
## Array
- [Write a function to remove duplicates in an array, sort it in the descending order.](#QA1)
- [How to empty an array.](#QA2)
- [Remove duplicate values from an array.](#QA3)
- [Shuffle elements in an array.](#QB5)

## Strings
- [Given a string, reverse each word in the sentence.](#QB13)
- [Given two strings, return true if they are anagrams of one another.](#QB14)
- [Find a maximum consecutive repeating char in a given string.](#QB15)

## Objects
- [Check if a given object is empty or not.](#QB11)

## Recursion
- [Write a function for factorial program.](#QC1)

## Binary Search

# Answers
#### QA1 
### ✍Write a function to remove duplicates in an array, sort it in the descending order.
<details><summary><b>Answer</b></summary>

```js
const arr = [5, 2, 7, 5, 8, 4, 7, 2];
let output = [];
for (i = 0; i < arr.length; i++) {
   if(output.indexOf(arr[i]) == -1) {
       output.push(arr[i]);
   }
}
console.log(output.sort((a, b) => { return b-a }));
```
</details>

**[⬆](#Questions)**
---
#### QAC1
### ✍Write a function for factorial program.
<details><summary><b>Answer</b></summary>

```js
let factorial = function(n) {
    if(n <= 0) {
        return 1;
    } else {
        return n * factorial(n-1);
    }
}
var result = factorial(6);
console.log(result);
```
</details>

**[⬆](#Questions)**
---
