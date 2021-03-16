# Filter, Map, Reduce

We say a language has "first-class functions" if it supports functions being passed as input or output values of other functions. JS has this feature, and JavaScripters take advantage of it all the time - for example, it's what allows us to pass a callback function as an input parameter for another function. It's also possible to have a function as a return value. A function which either takes or returns another function is called a **higher-order function**.

The higher-order functions \`filter()\`, \`map()\`, and \`reduce()\` are three of the most useful tools in a functional programmer's toolbox. Let's dig into how they work & how to use them.

</br>

In the exercises below we'll use the following \`wholes\` array of whole numbers (positive integers) to test our filtering, mapping, and reducing.

</br>

```javascript
wholes = Array(11) [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
wholes = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

</br>

### 1. Filter 

The \`filter\` function takes a "predicate" function (a function that takes in a value and returns a boolean) and an array, applies the predicate function to each value in the array, and returns a new array with only those values for which the predicate function returns \`true\`. 

</br>

The \`filter\` function has been implemented for you below:

```javascript
filter = ƒ(predicateFn, array)

function filter(predicateFn, array) {
  if (length(array) === 0) return [];
  const firstItem = head(array);
  const filteredFirst = predicateFn(firstItem) ? [firstItem] : [];
  return concat(filteredFirst, filter(predicateFn, tail(array)));
}
```


</br>


In the cells that follow, **fill in the TODOs** to implement predicate functions that filter the \`wholes\` array to produce the expected arrays.

```javascript
// ***************************
evens = Array(6) [0, 2, 4, 6, 8, 10]
odds = Array(5) [1, 3, 5, 7, 9]
greaterThanFour = Array(6) [5, 6, 7, 8, 9, 10]


// ***************************
isEven = ƒ(n)

function isEven(n) {
  return n % 2 === 0;
}

evens = filter(isEven, wholes)

odds = filter(n => {
  return !isEven(n);
}, wholes)

greaterThanFour = filter(n => n > 4, wholes)
```
🎉 evens ☝️ should be [0,2,4,6,8,10] </br>
🎉 odds  ☝️ should be [1,3,5,7,9] </br>
🎉 greaterThanFour ☝️ should be [5,6,7,8,9,10] </br>

</br>

```javascript
isPrime = ƒ(n)

function isPrime(n) {
  if (n <= 1) return false;
  const wholes = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  const possibleFactors = filter(m => m > 1 && m < n, wholes);
  const factors = filter(m => n % m === 0, possibleFactors);
  return factors.length === 0 ? true : false;
}

primes = Array(4) [2, 3, 5, 7]

primes = filter(isPrime, wholes)
```
🎉 primes ☝️ should be [2,3,5,7]





</br>



### 2. Map

The \`map\` function takes a one-argument function and an array, and applies the function to each element in the array, returning a new array of the resulting values. 

**Complete the body of the \`map\` function** below to produce the expected arrays in the cells that follow.

To move towards a functional mindset, use these helper functions instead of the  equivalent object-oriented array methods:
- \`head(array)\` to return the first element of an array (e.g. \`head([1,2,3]) -> 1\`)
- \`tail(array)\` to return the rest of the array after the first element (e.g. \`tail([1,2,3])\` returns \`[2,3]\`)
- \`length(array)\` to return the number of elements in the array (e.g. \`length([1,2,3])\` returns \`3\`)

Hint: remember that recursion is a functional programmer's best friend!




```javascript
// *********************************
doubled = Array(11) [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

// *********************************
map = ƒ(fn, array)

function map(fn, array) {
  if (length(array) === 0) return [];
  return [fn(head(array))].concat(map(fn, tail(array)));
}

// ********************************
doubled = map(n => n * 2, wholes)
```
🎉 halved ☝️ should be [0,0.5,1,1.5,2,2.5,3,3.5,4,4.5,5]

</br>

#### Challenge: Mapping Fizz Buzz

[Fizz Buzz](https://en.wikipedia.org/wiki/Fizz_buzz) is a whole-number counting game in which each number divisible by 3 is replaced which "fizz", each number divisible by 5 is replaced with "buzz", and each number divisible by both 3 and 5 is replaced with "fizzbuzz"

</br>

Complete the code below to **implement the Fizz Buzz game by mapping over the \`wholes\` array**.
```javascript
// **********************************
fizzBuzz = Array(11) ["fizzbuzz", 1, 2, "fizz", 4, "buzz", "fizz", 7, 8, "fizz", "buzz"]
Array(11) ["fizzbuzz", 1, 2, "fizz", 4, "buzz", "fizz", 7, 8, "fizz", "buzz"]

// **********************************
fizzBuzz = map(n => {
  const fizzed = n % 3 === 0 ? 'fizz' : '';
  const buzzed = n % 5 === 0 ? 'buzz' : '';
  return fizzed || buzzed ? fizzed + buzzed : n;
}, wholes)
```
🎉 fizzBuzz ☝️ should be [fizzbuzz,1,2,fizz,4,buzz,fizz,7,8,fizz,buzz]





```javascript

```





































#### Helper functions 
</br>

**concat = ƒ(array1, array2)**
```javascript

// Concatenate two arrays into a new single array
function concat(array1, array2) {
  return array1.concat(array2);
}
```


**length = ƒ(array)**
```javascript
// Return the number of items in an array
function length(array) {
  return array.length;
}
```


**head = ƒ(array)**
```javascript
// Return the first item in an array
function head(array) {
  return array[0];
}
```



```javascript
// **tail = ƒ(array)**
// Return the rest of an array after the first item
function tail(array) {
  return array.slice(1);
}
```
 </br>


##### **The functions below help give you feedback!**
```javascript
compareArrays = ƒ(actual, expected)

compareValues = ƒ(actual, expected)
```