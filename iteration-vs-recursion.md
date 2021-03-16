# Exercise: Iteration vs. Recursion

In functional programming, we avoid mutable state, and therefore avoid iterative loops using \`for\` or \`while\`. As an alternative to iteration, we use _recursion_ to break down the problem into smaller ones.

A recursive function has two parts:
- **Base case**: condition(s) under which the function returns an output without making a recursive call  
- **Recursive case**: condition(s) under which the function calls itself to return the output




## Comparing readability

Below are two versions of a function to compute the [factorial](https://en.wikipedia.org/wiki/Factorial) of a given positive integer \`n\`: one takes an iterative approach, the other uses recursion.

Take a moment to read & understand both functions. Feel free to add comments to explain what each line does, and/or try out the functions by calling them with different inputs. 

**Which one do you find more readable? Why?**


```javascript
iterativeFactorial = ƒ(n)

function iterativeFactorial(n) {
  let product = 1;
  while (n > 0) {
    product *= n;
    n--;
  }
  return product;
}

iterativeFactorial(3) // Try changing the input to test out the function
```


```javascript
recursiveFactorial = ƒ(n)

function recursiveFactorial(n) {
  if (n === 0) return 1;
  return n * recursiveFactorial(n - 1);
}

recursiveFactorial(3) // Try changing the input to test out the function
```








## Comparing writeability

Now it's time to try writing our own iterative & recursive functions!

In the cells below, fill in the code to implement iterative and recursive versions of a function to compute the Nth [Fibonacci number](https://en.wikipedia.org/wiki/Fibonacci_number) given a positive integer \`n\`.

Each Fibonacci number is defined as the sum of the previous two Fibonacci numbers, so \`fibonacci(n) = fibonacci(n-1) + fibonacci(n-2)\`. By convention, the first two numbers are fixed: \`fibonacci(0) = 0\` and \`fibonacci(1) = 1\`.

When each function has been implemented successfully, you'll see the tests below each function pass.


```javascript
iterativeFibonacci = ƒ(n)

function iterativeFibonacci(n) { 
  if (n === 0) return 0;
  if (n === 1) return 1;

  let previous = 0;
  let current = 1;
  for (let i = n; i > 1; i--) {
    let next = previous + current;
    previous = current;
    current = next;
  }
  return current;
```
🎉 iterativeFibonacci(2) should return 1

🎉 iterativeFibonacci(6) should return 8

🎉 iterativeFibonacci(10) should return 55

🎉 iterativeFibonacci(20) should return 6765


  

```javascript
iterativeFibonacci = ƒ(n)

function recursiveFibonacci(n) {
  if (n === 0) return 0;
  if (n === 1) return 1;
  return recursiveFibonacci(n - 2) + recursiveFibonacci(n - 1);
}
🎉 recursiveFibonacci(2) should return 1

🎉 recursiveFibonacci(6) should return 8

🎉 recursiveFibonacci(10) should return 55

🎉 recursiveFibonacci(20) should return 6765
```
  Once you've implemented both versions, take a moment to consider:
  
  Which did you find easier to write? Why?...








## Comparing performance

Using the number widget below to set the value of \`n\`, try calling your completed \`iterativeFibonacci()\` and \`recursiveFibonacci()\` functions with higher and higher values for \`n\`. 

Do very big numbers create a problem for either version?

With big numbers, the recursion do not assume the calculation for reasons...




There are two call recursion in the recursiveFibonacci function, doing the same work multiple times for each calculation...

It need here maybe to use the principal of memoization to cache the result and do not repeat the calculation



Then, there are too much functions calls on the call stack, open up each time some new execution context. The browser do not assume that in term of memory maybe or performance...

It need to read more about "Tail Call Optimization" and "Tail Recursive Function"...

