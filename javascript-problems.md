# Questions
## Array
- [Write a function to remove duplicates in an array, sort it in the descending order.](#QA1)
- [How to empty an array.](#QA2)
- [Remove duplicate values from an array.](#QA3)
- [Shuffle elements in an array.](#QA4)

## Strings
- [Given a string, reverse each word in the sentence. Example "emocleW ot aidnI". Return as "Welcome to India"](#QB1)
- [Given two strings, return true if they are anagrams of one another.](#QB2)
- [Find a maximum consecutive repeating char in a given string.](#QB3)

## Objects
- [Check if a given object is empty or not.](#QC1)

## Recursion
- [Write a function for factorial program.](#QD1)

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
#### QA2
### ✍How to empty an array.

**[⬆](#Questions)**
---
#### QA3
### ✍Remove duplicate values from an array.

**[⬆](#Questions)**
---
#### QA4
### ✍Shuffle elements in an array.

**[⬆](#Questions)**
---
#### QB1
### ✍Given a string, reverse each word in the sentence. Example ""emocleW ot aidnI". Return as "Welcome to India".
<details><summary><b>Answer</b></summary>

```js
let str = "emocleW ot aidnI";

let arr = str.split(' ');

let result = arr.map((item) => {
	return item.split('').reverse().join('');
});

console.log(result.join(' ')); // "Welcome to India"
```
</details>

**[⬆](#Questions)**
---
#### QB2
### ✍Given two strings, return true if they are anagrams of one another. 
<details><summary><b>Answer</b></summary>

```js
let strA = "monk";
let strB = "kmon";

function checkString(str) {
	return str.replace(/[^\w]/g).toLowerCase().split('').sort().join();
}

function isAnagram(strA, strB) {
	return checkString(strA) === checkString(strB);
}

console.log(isAnagram(strA, strB)); // true
```
</details>

**[⬆](#Questions)**
---
#### QB3
### ✍Find a maximum consecutive repeating char in a given string.
<details><summary><b>Answer</b></summary>

```js
/* Find occurance of each letter */
let str = "emocleW ot aidnI";

let replacedStr = str.replaceAll(' ', '');

// Method 1 - Using for loop
/* const resultObj = {};
let char, count;

for(let i = 0; i < replacedStr.length; i++) {
  char = replacedStr.charAt(i);

  resultObj[char] = count ? count + 1 : 1; 
} */

// Method 2 - Using reduce()
let result = [...replacedStr].reduce((total, curr) => {
	total[curr] = total[curr] ? total[curr] + 1 : 1;
    return total;
}, {});

console.log(result);
// {
//   a: 1,
//   c: 1,
//   d: 1,
//   e: 2,
//   i: 1,
//   I: 1,
//   l: 1,
//   m: 1,
//   n: 1,
//   o: 2,
//   t: 1,
//   W: 1
// }
```
</details>

**[⬆](#Questions)**
---
#### QC1
### ✍Check if a given object is empty or not.

**[⬆](#Questions)**
---
#### QD1
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
