## Technical Question
1. ### What is the significance of, and reason for, wrapping the entire content of a JavaScript source file in a function block?
<details><summary><b>Show Answer</b></summary>

The practice of wrapping the entire content of a JavaScript source file in a function block is called the "module pattern" or "immediately-invoked function expression" (IIFE) and it serves several purposes:

Encapsulation: By wrapping code in a function block, it creates a private scope for the variables and functions defined within it. This means that any variables or functions defined within the function block are not accessible outside of it, effectively encapsulating the code and preventing naming collisions with other code that may be present in the global scope.

Avoidance of global variables: When variables are declared outside of any function block, they become global variables, which can be accessed and modified by any other script running on the same page. By wrapping the code in a function block, variables and functions declared within it become private, avoiding the creation of new global variables.

Modularization: The module pattern allows for the creation of self-contained modules of code that can be reused across different parts of an application. By defining all the code related to a particular feature or component within a single function block, it becomes easier to manage and organize code.

Protection against minification issues: Some minification tools may rename variables in a way that could cause issues if the code is not wrapped in a function block. By using the module pattern, the code is protected from these issues as the variables are not exposed in the global scope.

Overall, wrapping the entire content of a JavaScript source file in a function block provides a way to write more organized, modular, and encapsulated code that is less prone to errors caused by global variables or minification issues.

</details>

2. ### What is the significance, and what are the benefits, of including 'use strict' at the beginning of a JavaScript source file?
<details><summary><b>Show Answer</b></summary>
The 'use strict' statement is a feature introduced in ECMAScript 5 that allows developers to opt into a stricter version of JavaScript, which helps to avoid common mistakes and improve performance. When 'use strict' is included at the beginning of a JavaScript file, it enables strict mode for that entire file. Some benefits of using strict mode are:

It helps to catch common coding mistakes that would otherwise result in silent errors, such as using undeclared variables, assigning values to read-only properties, or using duplicate function parameter names.
It disallows certain unsafe or confusing language features, such as using the 'eval' function or implicit type coercion.
It improves performance in some cases by allowing JavaScript engines to optimize code more aggressively.</details>

3. ### What is NaN? What is its type? How can you reliably test if a value is equal to NaN?
<details><summary><b>Show Answer</b></summary>
NaN stands for "Not a Number" and is a special value in JavaScript that represents an undefined or unrepresentable value resulting from a mathematical operation. Despite its name, NaN is of the type "number". However, NaN is unique in that it is the only value in JavaScript that is not equal to itself. Therefore, a reliable way to test if a value is equal to NaN is to use the 'isNaN()' function, which returns true if the value is NaN and false otherwise.</details>

4. ### What is a “closure” in JavaScript? Provide an example.
<details><summary><b>Show Answer</b></summary>
A closure is a feature in JavaScript that allows a function to retain access to variables defined in its outer scope even after the outer function has returned. This is achieved by creating a new execution context for the inner function, which includes a reference to the outer function's lexical environment. Here's an example of a closure:

```
  function outerFunction() {
  const name = 'John';
  
  function innerFunction() {
    console.log(`Hello ${name}!`);
  }
  
  return innerFunction;
}

const greeting = outerFunction();
greeting(); // Output: "Hello John!"
```

In this example, outerFunction returns innerFunction, which is then assigned to the greeting variable. When greeting is called, it still has access to the name variable, even though outerFunction has already returned.
</details>

5. ### How do you clone an object?
<details><summary><b>Show Answer</b></summary>
In JavaScript, objects are reference types, which means that assigning an object to a new variable only creates a reference to the original object, not a new copy. To create a clone of an object, you can use several methods, including:

 - Using the Object.assign() method:

```
const original = { a: 1, b: 2 };
const clone = Object.assign({}, original);
```
  
 - Using the spread operator:
  
```
const original = { a: 1, b: 2 };
const clone = { ...original };
```

 - Using JSON.stringify() and JSON.parse():

 ```
const original = { a: 1, b: 2 };
const clone = JSON.parse(JSON.stringify(original));
 ```

</details>

6. ### How do you add an element at the begining of an array? How do you add one at the end?
<details><summary><b>Show Answer</b></summary>
To add an element at the beginning of an array in JavaScript, you can use the unshift() method, which adds one or more elements to the beginning of an array and returns the new length of the array. Here's an example:

```
const arr = [2, 3, 4];
arr.unshift(1);
console.log(arr); // Output: [1, 2, 3, 4]
```
To add an element to the end of an array, you can use the push() method, which adds one or more elements to the end of an array and returns the new length of the array. Here's an example:

```
const myArray = [1, 2, 3];
myArray.push(4);
console.log(myArray); // [1, 2, 3, 4]
```

</details>

7. ### What is the difference between undefined and not defined in JavaScript?
<details><summary><b>Show Answer</b></summary>

Undefined and not defined are both ways of referring to a variable that has not been assigned a value, but they are used in different contexts. Undefined means that a variable has been declared but has not been assigned a value, while not defined means that a variable has not been declared at all. Here's an example:

```
let myVariable;
console.log(myVariable); // undefined

console.log(myOtherVariable); // Uncaught ReferenceError: myOtherVariable is not defined
```
  
In the first example, myVariable has been declared but has not been assigned a value, so its value is undefined. In the second example, myOtherVariable has not been declared at all, so trying to access it will result in a ReferenceError.

</details>

8. ### How do you check if an object is an array or not?
<details><summary><b>Show Answer</b></summary>
You can check if an object is an array by using the Array.isArray() method. This method returns true if the object is an array, and false if it is not. Here's an example:

```
const myArray = [1, 2, 3];
console.log(Array.isArray(myArray)); // true

const myObject = { foo: 'bar' };
console.log(Array.isArray(myObject)); // false
```
</details>

9. ### What is function hoisting in JavaScript?
<details><summary><b>Show Answer</b></summary>
Function hoisting is a JavaScript behavior where function declarations are moved to the top of their scope before the code is executed. This means that you can call a function before it is declared in your code. For example:

```
foo(); // 'bar'

function foo() {
  console.log('bar');
}
```

In this example, we can call the foo() function before it is declared because the function declaration is hoisted to the top of the scope. Note that function expressions, which are assigned to a variable, are not hoisted.

</details>

10. ### Explain how `this` works in JavaScript
<details><summary><b>Show Answer</b></summary>
In JavaScript, the this keyword refers to the object that is currently executing the code. The value of this can change depending on how a function is called.

If a function is called as a method of an object, this refers to the object itself:
</details>

11. ### Explain how prototypal inheritance works
<details><summary><b>Show Answer</b></summary>

</details>

12. ### Explain why the following doesn't work as an IIFE: "function foo(){ }();". What needs to be changed to properly make it an IIFE?
<details><summary><b>Show Answer</b></summary>

</details>

13. ### What's the difference between a variable that is: null, undefined or undeclared? How would you go about checking for any of these states?
<details><summary><b>Show Answer</b></summary>

</details>

14. ### Can you describe the main difference between a .forEach loop and a .map() loop and why you would pick one versus the other?
<details><summary><b>Show Answer</b></summary>

</details>

15. ### What's a typical use case for anonymous functions?
<details><summary><b>Show Answer</b></summary>

</details>

16. ### How do you organize your code? (module pattern, classical inheritance?)
<details><summary><b>Show Answer</b></summary>

</details>

17. ### Difference between: function Person(){}, var person = Person(), and var person = new Person()?
<details><summary><b>Show Answer</b></summary>

</details>

18. ### What's the difference between .call and .apply?
<details><summary><b>Show Answer</b></summary>

</details>

19. ### Explain Function.prototype.bind.
<details><summary><b>Show Answer</b></summary>

</details>

20. ### When would you use document.write()?
<details><summary><b>Show Answer</b></summary>

</details>

21. ### Explain Ajax in as much detail as possible.
<details><summary><b>Show Answer</b></summary>

</details>

22. ### What are the advantages and disadvantages of using Ajax?
<details><summary><b>Show Answer</b></summary>

</details>

23. ### What's the difference between an "attribute" and a "property"?
<details><summary><b>Show Answer</b></summary>

</details>

24. ### What is the difference between == and ===?
<details><summary><b>Show Answer</b></summary>

</details>

25. ### Create a for loop that iterates up to 100 while outputting "fizz" at multiples of 3, "buzz" at multiples of 5 and "fizzbuzz" at multiples of 3 and 5
<details><summary><b>Show Answer</b></summary>

</details>

26. ### Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
<details><summary><b>Show Answer</b></summary>

</details>

27. ### Explain what a single page app is and how to make one SEO-friendly.
<details><summary><b>Show Answer</b></summary>

</details>

28. ### What are the pros and cons of using Promises instead of callbacks?
<details><summary><b>Show Answer</b></summary>

</details>

29. ### What tools and techniques do you use debugging JavaScript code?
<details><summary><b>Show Answer</b></summary>

</details>

30. ### What language constructions do you use for iterating over object properties and array items?
<details><summary><b>Show Answer</b></summary>

</details>

31. ### Explain the difference between mutable and immutable objects.
<details><summary><b>Show Answer</b></summary>

</details>

32. ### Explain the difference between synchronous and asynchronous functions.
<details><summary><b>Show Answer</b></summary>

</details>

33. ### What is event loop? What is the difference between call stack and task queue?
<details><summary><b>Show Answer</b></summary>

</details>

34. ### What are the differences between variables created using let, var or const?
<details><summary><b>Show Answer</b></summary>

</details>

35. ### What are the differences between ES6 class and ES5 function constructors?
<details><summary><b>Show Answer</b></summary>

</details>

36. ### What is the definition of a higher-order function?
<details><summary><b>Show Answer</b></summary>

</details>

37. ### Can you give an example of a curry function and why this syntax offers an advantage?
<details><summary><b>Show Answer</b></summary>

</details>

38. ### Can you describe the Document Object Model in JavaScript?
<details><summary><b>Show Answer</b></summary>

</details>

39. ### What is the difference between function scope and block scope in JavaScript?
<details><summary><b>Show Answer</b></summary>

</details>

40. ### What will this do and why? var foo = 10 + '20';
<details><summary><b>Show Answer</b></summary>

</details>
