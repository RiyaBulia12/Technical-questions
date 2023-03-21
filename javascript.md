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
In JavaScript, this refers to the current execution context, which is usually determined by how a function is called. The value of this can vary depending on how a function is invoked, and can be difficult to predict without understanding the underlying rules.

Here are the basic rules for determining the value of this:

Global context: If this is used outside of any function or object, it refers to the global object. In a browser, the global object is the window object.

Object method: If this is used inside of an object method, it refers to the object that the method is a property of. For example:

```
const person = {
  name: "John",
  greet: function() {
    console.log(`Hello, my name is ${this.name}.`);
  }

person.greet(); // logs "Hello, my name is John."
```  
person.greet(); // logs "Hello, my name is John."
person.greet(); // logs "Hello, my name is John."
Constructor function: If this is used inside of a constructor function, it refers to the instance of the object that is being created. For example:
```
function Person(name) {
  this.name = name;
  this.greet = function() {
    console.log(`Hello, my name is ${this.name}.`);
  }
}

const john = new Person("John");
john.greet(); // logs "Hello, my name is John."
```
Function invocation: If this is used inside of a regular function that is not a method of an object or a constructor function, it refers to the global object. However, if the function is called with the call or apply method, the value of this can be set explicitly to a specific object.
```
function greet() {
  console.log(`Hello, my name is ${this.name}.`);
}

const person1 = { name: "John" };
const person2 = { name: "Jane" };

greet(); // logs "Hello, my name is undefined."
greet.call(person1); // logs "Hello, my name is John."
greet.apply(person2); // logs "Hello, my name is Jane."
```
It's important to note that arrow functions do not have their own this binding, and instead inherit the this value from their enclosing lexical scope. This means that the value of this inside of an arrow function depends on where the function is defined, rather than how it is called.

In summary, the value of this in JavaScript depends on how a function is called, and can be determined by following the rules outlined above.

More detailed explaination onn Freecodecamp: https://www.freecodecamp.org/news/javascript-this-keyword-binding-rules/
</details>

11. ### Explain how prototypal inheritance works
<details><summary><b>Show Answer</b></summary>
Prototypal inheritance is a type of inheritance model in JavaScript where objects can inherit properties and methods from their prototypes. Each object in JavaScript has a prototype, which is essentially a reference to another object. When an object is created, it automatically inherits all the properties and methods of its prototype.

Here's an example:

```
// Create a parent object
let parent = {
  firstName: "John",
  lastName: "Doe",
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
};

// Create a child object
let child = Object.create(parent);

// Add a property to the child object
child.age = 25;

console.log(child.firstName); // "John"
console.log(child.age); // 25
console.log(child.fullName()); // "John Doe"
```
In this example, we first create a parent object with properties and a method. Then, we create a child object using Object.create(parent). This creates a new object with its prototype set to the parent object. We then add a new property to the child object.

When we access the firstName property of the child object, JavaScript first checks if it exists on the object itself. Since it doesn't, it checks the prototype chain and finds it on the parent object. Similarly, when we call the fullName() method on the child object, JavaScript finds it on the parent object through the prototype chain.

Prototypal inheritance is useful because it allows us to reuse code and create objects that share common properties and methods without having to define them on each individual object. It also allows us to create more complex inheritance relationships by chaining together prototypes. However, it's important to be aware of the potential pitfalls, such as unintentional modification of shared properties and methods.

</details>

12. ### Explain why the following doesn't work as an IIFE: "function foo(){ }();". What needs to be changed to properly make it an IIFE?
<details><summary><b>Show Answer</b></summary>
IIFE stands for Immediately Invoked Function Expression. It is a design pattern commonly used in JavaScript to create a function that is executed as soon as it is defined.

The following code doesn't work as an IIFE:

```
function foo() { }();
```
This is because the function is defined first and then immediately called with empty parentheses, which causes a syntax error. The JavaScript interpreter thinks that the function is being called with no arguments, but since there are no parentheses around the function definition, it doesn't know that it's actually supposed to be an IIFE.

To properly make it an IIFE, we need to wrap the entire function in parentheses like this:

```
(function foo() { })();
```
This tells the JavaScript interpreter that the function is meant to be an expression and not a declaration, and that it should be invoked immediately after it is defined.

Alternatively, we can also use the more commonly used syntax:
```
(function() { })();
```
This creates an anonymous function expression that is immediately invoked.

In summary, to make a function an IIFE, we need to wrap it in parentheses to create a function expression and then immediately invoke it.
</details>

13. ### What's the difference between a variable that is: null, undefined or undeclared? How would you go about checking for any of these states?
<details><summary><b>Show Answer</b></summary>
In JavaScript, there are three different states that a variable can be in: null, undefined, or undeclared. Let's discuss each state and how you can check for them:

1. Null: A null value is assigned by a programmer and represents an intentional absence of any object value. It is a value that represents no value or no object. In other words, null is explicitly set by the programmer to indicate that there is no value assigned to the variable.
To check if a variable is null, you can use the strict equality operator (===) to compare the variable to the null value. For example:

```
let myVariable = null;

if (myVariable === null) {
  console.log("myVariable is null");
}
```
2. Undefined: A variable is undefined when it has been declared but has not been assigned a value. It can also be undefined when a function doesn't return a value or when an object property doesn't exist.
To check if a variable is undefined, you can use the typeof operator and compare it to the string "undefined". For example:

```
let myVariable;

if (typeof myVariable === "undefined") {
  console.log("myVariable is undefined");
}
```
3. Undeclared: A variable is undeclared if it has not been declared using the var, let, or const keyword. It means that the variable doesn't exist in the current scope.
To check if a variable is undeclared, you can use a try-catch block and catch the ReferenceError that is thrown when an undeclared variable is referenced. For example:

```
try {
  if (myUndeclaredVariable === undefined) {
    console.log("myUndeclaredVariable is undefined");
  }
} catch (e) {
  console.log("myUndeclaredVariable is undeclared");
}
```
}
In summary, to check for each state:

To check for null: use strict equality (===) and compare to the null value.
To check for undefined: use typeof operator and compare to the string "undefined".
To check for undeclared: use a try-catch block and catch the ReferenceError thrown when an undeclared variable is referenced.
</details>

14. ### Can you describe the main difference between a .forEach loop and a .map() loop and why you would pick one versus the other?
<details><summary><b>Show Answer</b></summary>
The main difference between a .forEach loop and a .map() loop is in their return values and the way they treat the original array.

A .forEach loop is used when you want to perform a certain action on every element of an array, but you don't necessarily want to create a new array based on the original one. It simply iterates over each item in the array and performs the specified action. The return value of a .forEach loop is always undefined.

A .map() loop, on the other hand, is used when you want to create a new array based on the original one, by applying a certain function to each element of the array. It returns a new array with the same length as the original, but with the elements transformed by the function.

So, why would you pick one over the other?

If you simply need to perform an action on each element of an array, without creating a new array, then a .forEach loop is the way to go. It can be used for simple tasks like logging each element in the array to the console, or more complex tasks like modifying the original array.

If you need to create a new array based on the original one, by transforming each element in some way, then a .map() loop is the better choice. It can be used for tasks like converting an array of Celsius temperatures to an array of Fahrenheit temperatures, or transforming an array of objects to an array of specific object properties.

It's worth noting that neither of these methods modifies the original array, so they are both safe to use in that regard.
</details>

15. ### What's a typical use case for anonymous functions?
<details><summary><b>Show Answer</b></summary>
Anonymous functions, also known as lambda functions, are functions without a name that can be created and passed as arguments to other functions or used inline in expressions. A typical use case for anonymous functions is when we need to define a small and simple function that is only needed once and doesn't require a full-fledged function definition.

One common use case for anonymous functions is in functional programming, where higher-order functions are frequently used. Higher-order functions are functions that take one or more functions as arguments and/or return a function as a result. In such cases, anonymous functions can be used as "throwaway" functions to define the behavior of the higher-order function on the fly.

For example, let's say we have a list of numbers and we want to filter out only the even numbers. We could use the built-in filter function in Python and pass an anonymous function as the filter condition, like this:

```
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = filter(lambda x: x % 2 == 0, numbers)
print(list(even_numbers))  # [2, 4, 6]
```
In this example, we define an anonymous function lambda x: x % 2 == 0 that takes a single argument x and returns True if x is even (i.e., if x % 2 == 0). We then pass this anonymous function as the filter condition to the filter function, which returns an iterator over the even numbers in the numbers list. Finally, we convert the iterator to a list and print it.

Another use case for anonymous functions is when defining callbacks or event handlers. For example, if we are working with a GUI toolkit that allows us to attach a callback function to a button press event, we could define the callback function inline as an anonymous function instead of creating a named function and passing it as an argument.

Overall, anonymous functions are a useful tool in programming that allows us to write more concise and readable code in certain situations where we don't need a named function or where a named function would be too cumbersome to define.
</details>

16. ### How do you organize your code? (module pattern, classical inheritance?)
<details><summary><b>Show Answer</b></summary>
When it comes to organizing code, there are several patterns and approaches you can use. The choice ultimately depends on the specifics of the project and the needs of the team.

One popular approach is the module pattern, where you group related functions and variables into a self-contained module. This pattern allows for better encapsulation, making it easier to reason about and maintain the codebase. With this approach, you can create modules for various parts of your application, such as user authentication, data storage, or UI components. Each module can have its own public interface and private implementation, which helps to prevent unwanted interactions between modules.

Another popular approach is classical inheritance, which involves creating classes and hierarchies of objects that inherit properties and methods from parent classes. This approach is useful when you need to create many similar objects with shared properties and behavior. It can also help with code reuse, as you can create parent classes that define common functionality and then inherit from them to create more specialized subclasses.

In addition to these approaches, there are also other patterns you can use, such as functional programming, dependency injection, and observer pattern. The important thing is to choose the approach that makes the most sense for your project and to be consistent in your coding practices across the codebase.
</details>

17. ### Difference between: function Person(){}, var person = Person(), and var person = new Person()?
<details><summary><b>Show Answer</b></summary>
In JavaScript, a function can be used to create objects, which can then be used to store data or perform actions. The three code snippets you provided are all related to creating objects using a function, but they differ in how they create and initialize the object.

1. function Person() {} is a function declaration that defines a function called "Person". This function doesn't do anything by default; it simply exists as a named function. You can think of it as a blueprint for creating objects of type "Person", but it doesn't create any objects on its own. This function can be used to create new objects using the new keyword.

2. var person = Person(); is a variable declaration that creates a variable called "person" and assigns it the return value of calling the "Person" function. However, since the "Person" function doesn't return anything explicitly, this line of code will set the "person" variable to undefined. This code snippet doesn't create a new object of type "Person" either.

3. var person = new Person(); is a variable declaration that creates a variable called "person" and assigns it a new instance of the "Person" object created with the new keyword. The new keyword is used to create a new instance of an object based on a constructor function. When a constructor function is called with the new keyword, it creates and returns a new object instance.

When creating objects using constructor functions, it is generally recommended to use the new keyword to ensure that a new instance of the object is created. Using the new keyword creates a new object and sets the value of this to the new object, allowing the constructor to initialize the new object properly.
</details>


18. ### What's the difference between .call and .apply?
<details><summary><b>Show Answer</b></summary>

</details>

19. ### Explain Function.prototype.bind.
<details><summary><b>Show Answer</b></summary>
Function.prototype.bind is a built-in method in JavaScript that returns a new function with a specified this value and an optional set of arguments. This method allows us to bind a function to a specific object and create a new function that will use the specified object as its this value.

The syntax for bind is as follows:
```
function.bind(thisArg[, arg1[, arg2[, ...]]])
```
Here, thisArg is the object that the function will use as its this value when it is called. The remaining arguments arg1, arg2, etc. are optional and represent the arguments that will be passed to the function when it is called.

Let's look at an example to better understand bind. Suppose we have an object person with a property name and a method greet:
```
const person = {
  name: 'John',
  greet: function() {
    console.log(`Hello, my name is ${this.name}.`);
  }
};
```
If we call person.greet() directly, we'll see Hello, my name is John. printed to the console.

Now let's say we want to create a new function that has person as its this value, but we don't want to call the greet method directly. We can use bind to create a new function:

```
const greetPerson = person.greet.bind(person);
```
Here, greetPerson is a new function that has person as its this value. We can call it just like we called person.greet():

```
greetPerson(); // logs "Hello, my name is John."
```
The advantage of using bind is that we can pass greetPerson around as a reference to a function that is bound to person. We can use it in callback functions, pass it as an argument to other functions, etc.

In summary, Function.prototype.bind is a powerful method in JavaScript that allows us to bind a function to a specific object and create a new function with a specified this value and set of arguments.
</details>

20. ### When would you use document.write()?
<details><summary><b>Show Answer</b></summary>
document.write() is a method in JavaScript that writes content directly to an HTML document. It can be used in a variety of scenarios, including but not limited to:

1. During page load: document.write() can be used during the loading of a page to add content dynamically. This is particularly useful when you want to include some dynamic content that is generated using JavaScript or some other scripting language.

2. Testing purposes: document.write() can be used during development to quickly test some functionality. For example, if you want to see if a particular piece of JavaScript code is working as expected, you can use document.write() to display some output on the page.

3. Dynamic content generation: document.write() can be used to generate dynamic content on the fly. For instance, if you have a button that, when clicked, generates some content on the page, you can use document.write() to write that content directly to the document.

4. External script loading: document.write() can be used to load external scripts dynamically. For example, if you want to load a script file dynamically after the page has loaded, you can use document.write() to write the script tag directly to the document.

It's important to note that document.write() can have some drawbacks and limitations, particularly when used after the page has finished loading. In some cases, it can overwrite existing content on the page, causing unexpected behavior. Additionally, it can be difficult to maintain and modify code that relies heavily on document.write(). Therefore, it's generally recommended to use other methods, such as DOM manipulation, to add content to a web page dynamically.
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
