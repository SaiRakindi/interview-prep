# JS most asked interview questions

Created: November 13, 2024 10:41 AM

### 1. **Difference between 'Pass by Value' and 'Pass by Reference'**

- **Pass by Value**: A copy of the actual value is passed. Changes made to the parameter inside the function have no effect on the actual value.
    
    ```jsx
    let a = 5;
    function changeValue(val) {
        val = 10;
    }
    changeValue(a);
    console.log(a); // Output: 5
    
    ```
    
- **Pass by Reference**: A reference to the actual value is passed. Changes made to the parameter affect the actual value.
    
    ```jsx
    let obj = { x: 5 };
    function changeValue(ref) {
        ref.x = 10;
    }
    changeValue(obj);
    console.log(obj.x); // Output: 10
    
    ```
    

### 2. **Difference between `map` and `filter`**

- **`map`**: Creates a new array by applying a function to each element of the array.
    
    ```jsx
    const numbers = [1, 2, 3, 4];
    const doubled = numbers.map(n => n * 2);
    console.log(doubled); // Output: [2, 4, 6, 8]
    
    ```
    
- **`filter`**: Creates a new array containing only elements that pass a certain condition.
    
    ```jsx
    const numbers = [1, 2, 3, 4];
    const evens = numbers.filter(n => n % 2 === 0);
    console.log(evens); // Output: [2, 4]
    
    ```
    

### 3. **Difference between `map()` and `forEach()`**

- **`map()`**: Returns a new array with the results of calling a provided function on every element in the array.
    
    ```jsx
    const numbers = [1, 2, 3];
    const squared = numbers.map(n => n * n);
    console.log(squared); // Output: [1, 4, 9]
    
    ```
    
- **`forEach()`**: Executes a provided function once for each array element, but doesn’t return anything.
    
    ```jsx
    const numbers = [1, 2, 3];
    numbers.forEach(n => console.log(n * n));
    // Output: 1, 4, 9 (but returns undefined)
    
    ```
    

### 4. **Difference between Pure and Impure Functions**

- **Pure Function**: Given the same inputs, always returns the same output and has no side effects.
    
    ```jsx
    function pure(a, b) {
        return a + b;
    }
    
    ```
    
- **Impure Function**: May have side effects or return different outputs for the same inputs.
    
    ```jsx
    let x = 10;
    function impure(a) {
        return a + x; // Depends on an external variable
    }
    
    ```
    

### 5. **Difference between `for-in` and `for-of`**

- **`for-in`**: Iterates over all enumerable properties of an object.
    
    ```jsx
    let obj = {a: 1, b: 2, c: 3};
    for (let key in obj) {
        console.log(key); // Output: 'a', 'b', 'c'
    }
    
    ```
    
- **`for-of`**: Iterates over the values of an iterable object (like arrays, strings).
    
    ```jsx
    let arr = [10, 20, 30];
    for (let value of arr) {
        console.log(value); // Output: 10, 20, 30
    }
    
    ```
    

### 6. **Differences between `call()`, `apply()`, and `bind()`**

- **`call()`**: Calls a function with a given `this` value and arguments provided individually.
    
    ```jsx
    function greet(greeting) {
        console.log(greeting + ', ' + this.name);
    }
    const person = { name: 'John' };
    greet.call(person, 'Hello'); // Output: Hello, John
    
    ```
    
- **`apply()`**: Similar to `call()`, but arguments are provided as an array.
    
    ```jsx
    greet.apply(person, ['Hi']); // Output: Hi, John
    
    ```
    
- **`bind()`**: Returns a new function with a specific `this` value and optional arguments.
    
    ```jsx
    const greetPerson = greet.bind(person, 'Hey');
    greetPerson(); // Output: Hey, John
    
    ```
    

### 7. **Key Features of ES6**

- **Arrow functions**:
    
    ```jsx
    const add = (a, b) => a + b;
    
    ```
    
- **Template literals**:
    
    ```jsx
    const name = 'World';
    console.log(`Hello, ${name}!`); // Output: Hello, World!
    
    ```
    
- **Destructuring assignment**:
    
    ```jsx
    const [a, b] = [1, 2];
    
    ```
    
- **Default parameters**:
    
    ```jsx
    function greet(name = 'Guest') {
        return `Hello, ${name}`;
    }
    
    ```
    
- **Promises**:
    
    ```jsx
    const promise = new Promise((resolve, reject) => {
        // Async code
    });
    
    ```
    

### 8. **Spread Operator in JavaScript**

- Expands an array or object into its elements.
    
    ```jsx
    const arr = [1, 2, 3];
    const newArr = [...arr, 4, 5];
    console.log(newArr); // Output: [1, 2, 3, 4, 5]
    
    ```
    

### 9. **Rest Operator in JavaScript**

- Collects multiple elements into an array.
    
    ```jsx
    function sum(...args) {
        return args.reduce((a, b) => a + b, 0);
    }
    console.log(sum(1, 2, 3)); // Output: 6
    
    ```
    

### 10. **DRY, KISS, YAGNI, SOLID Principles**

- **DRY (Don't Repeat Yourself)**: Avoid duplication of code.
- **KISS (Keep It Simple, Stupid)**: Simplicity should be a key goal.
- **YAGNI (You Aren't Gonna Need It)**: Don't implement features until necessary.
- **SOLID**:
    - **S**: Single Responsibility Principle.
    - **O**: Open/Closed Principle.
    - **L**: Liskov Substitution Principle.
    - **I**: Interface Segregation Principle.
    - **D**: Dependency Inversion Principle.

### 11. **What is Temporal Dead Zone?**

- Refers to the time between entering a scope and variable declaration where the variable cannot be accessed.
    
    ```jsx
    console.log(a); // ReferenceError: Cannot access 'a' before initialization
    let a = 5;
    
    ```
    

### 12. **Different Ways to Create an Object in JavaScript**

- **Object literal**:
    
    ```jsx
    const obj = { key: 'value' };
    
    ```
    
- **Constructor function**:
    
    ```jsx
    function Obj() {
        this.key = 'value';
    }
    const obj = new Obj();
    
    ```
    
- **Object.create()**:
    
    ```jsx
    const obj = Object.create(null);
    
    ```
    
- **Class**:
    
    ```jsx
    class Obj {
        constructor() {
            this.key = 'value';
        }
    }
    const obj = new Obj();
    
    ```
    

### 13. **Difference between `Object.keys()`, `values()`, and `entries()`**

- **`Object.keys()`**: Returns an array of an object's keys.
    
    ```jsx
    const obj = { a: 1, b: 2 };
    console.log(Object.keys(obj)); // Output: ['a', 'b']
    
    ```
    
- **`Object.values()`**: Returns an array of an object's values.
    
    ```jsx
    console.log(Object.values(obj)); // Output: [1, 2]
    
    ```
    
- **`Object.entries()`**: Returns an array of an object's key-value pairs.
    
    ```jsx
    console.log(Object.entries(obj)); // Output: [['a', 1], ['b', 2]]
    
    ```
    

### 14. **Difference between `Object.freeze()` and `Object.seal()`**

- **`Object.freeze()`**: Makes an object immutable; cannot add, remove, or change properties.
    
    ```jsx
    const obj = Object.freeze({ a: 1 });
    obj.a = 2; // Error in strict mode
    
    ```
    
- **`Object.seal()`**: Allows changing existing properties but prevents adding or removing properties.
    
    ```jsx
    const obj = Object.seal({ a: 1 });
    obj.a = 2; // Allowed
    obj.b = 3; // Not allowed
    
    ```
    

### 15. **What is a Polyfill in JavaScript?**

- A polyfill is code that provides modern functionality on older browsers that do not natively support it.
    
    ```jsx
    if (!Array.prototype.includes) {
        Array.prototype.includes = function(element) {
            return this.indexOf(element) !== -1;
        };
    }
    
    ```
    

### 16. **What is a Generator Function in JavaScript?**

- A function that can be paused and resumed, using the `function*` syntax.

```jsx
 function* generator() {
     yield 1;
     yield 2;
     return 3;
 }
 const gen = generator();
 console.log(gen.next().value); // Output: 1

```

### 17. **What is a Prototype in JavaScript?**

- The mechanism by which objects in JavaScript inherit properties and methods from one another.
    
    ```jsx
    function Person(name) {
        this.name = name;
    }
    Person.prototype.greet = function() {
        console.log('Hello, ' + this.name);
    };
    const john = new Person('John');
    john.greet(); // Output: Hello, John
    
    ```
    

### 18. **What is an IIFE (Immediately Invoked Function Expression)?**

- A function that is executed immediately after its creation.
    
    ```jsx
    (function() {
        console.log('IIFE');
    })(); // Output: IIFE
    
    ```
    

### 19. **What is CORS?**

- **Cross-Origin Resource Sharing (CORS)**: A security feature that allows or restricts resources on a web page to be requested from another domain outside the domain from which the resource originated.

### 20. **Different Data Types in JavaScript**

- **Primitive Types**: `String`, `Number`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`.
- **Reference Types**: `Object`, `Array`, `Function`.

### 21. **Differences between TypeScript and JavaScript**

- **TypeScript**: A statically typed superset of JavaScript that compiles to plain JavaScript. Adds types and other features to JavaScript.
- **JavaScript**: A dynamically typed scripting language.

### 22. **Authentication vs Authorization**

- **Authentication**: Verifying who a user is (e.g., login process).
- **Authorization**: Determining what resources a user can access (e.g., permissions).

### 23. **Difference between `null` and `undefined`**

- **`null`**: Explicitly indicates the absence of any object value.
- **`undefined`**: Indicates that a variable has been declared but not yet assigned a value.

### 24. **Output of `3+2+"7"`**

- **Output**: `"57"` (because `3+2` is `5`, and `5+"7"` results in string concatenation).

### 25. **Slice vs Splice in JavaScript**

- **`slice()`**: Returns a shallow copy of a portion of an array.
    
    ```jsx
    const arr = [1, 2, 3, 4];
    const newArr = arr.slice(1, 3);
    console.log(newArr); // Output: [2, 3]
    
    ```
    
- **`splice()`**: Changes the contents of an array by removing, replacing, or adding elements.
    
    ```jsx
    const arr = [1, 2, 3, 4];
    arr.splice(1, 2);
    console.log(arr); // Output: [1, 4]
    
    ```
    

### 26. **What is Destructuring?**

- A syntax for extracting values from arrays or objects into distinct variables.
    
    ```jsx
    const [a, b] = [1, 2];
    const {name, age} = {name: 'John', age: 25};
    
    ```
    

### 27. **What is `setTimeout` in JavaScript?**

- Executes a function after a specified delay.
    
    ```jsx
    setTimeout(() => {
        console.log('Hello');
    }, 1000); // Output: Hello (after 1 second)
    
    ```
    

### 28. **What is `setInterval` in JavaScript?**

- Repeatedly executes a function with a fixed time delay between each call.
    
    ```jsx
    const intervalId = setInterval(() => {
        console.log('Hello');
    }, 1000); // Output: Hello (every 1 second)
    
    ```
    

### 29. **What are Promises in JavaScript?**

- A promise represents the eventual completion (or failure) of an asynchronous operation and its resulting value.
    
    ```jsx
    const promise = new Promise((resolve, reject) => {
        setTimeout(() => resolve('Done!'), 1000);
    });
    promise.then(result => console.log(result)); // Output: Done! (after 1 second)
    
    ```
    

### 30. **What is a Call Stack in JavaScript?**

- A stack data structure that records the function calls in a program.
    
    ```jsx
    function first() {
        second();
    }
    function second() {
        console.log('Second function');
    }
    first();
    // Call Stack: first -> second -> log
    
    ```
    

### 31. **What is a Closure?**

- A closure is a function that retains access to its lexical scope, even when the function is executed outside that scope.
    
    ```jsx
    function outer() {
        let count = 0;
        return function inner() {
            count++;
            console.log(count);
        };
    }
    const counter = outer();
    counter(); // Output: 1
    counter(); // Output: 2
    
    ```
    

### 32. **What are Callbacks in JavaScript?**

- A callback is a function passed as an argument to another function, to be executed after an operation is completed.
    
    ```jsx
    function greet(name, callback) {
        console.log('Hello ' + name);
        callback();
    }
    greet('John', function() {
        console.log('Callback function executed');
    });
    
    ```
    

### 33. **What are Higher-Order Functions in JavaScript?**

- Functions that take other functions as arguments or return functions as their result.
    
    ```jsx
    function higherOrder(fn) {
        return function() {
            return fn() + '!';
        };
    }
    const excited = higherOrder(() => 'Hello');
    console.log(excited()); // Output: Hello!
    
    ```
    

### 34. **Difference between `==` and `===` in JavaScript**

- **`==`**: Abstract equality operator (performs type conversion if necessary).
    
    ```jsx
    console.log(5 == '5'); // Output: true
    
    ```
    
- **`===`**: Strict equality operator (no type conversion).
    
    ```jsx
    console.log(5 === '5'); // Output: false
    
    ```
    

### 35. **Is JavaScript Dynamically Typed or Statically Typed?**

- **Dynamically Typed**: The type of a variable is determined at runtime.
    
    ```jsx
    let a = 10; // a is a number
    a = 'Hello'; // a is now a string
    
    ```
    

### 36. **Difference between `IndexedDB` and `sessionStorage`**

- **`IndexedDB`**: A low-level API for client-side storage of large amounts of structured data, including files/blobs.
- **`sessionStorage`**: Stores data for the duration of the page session.

### 37. **What are Interceptors?**

- **Interceptors**: Functions that intercept HTTP requests or responses before they are handled by `then` or `catch` in a `Promise`.

### 38. **What is Hoisting?**

- A behavior in JavaScript where variable and function declarations are moved to the top of their scope before code execution.
    
    ```jsx
    console.log(a); // Output: undefined
    var a = 5;
    
    ```
    

### 39. **Differences between `let`, `var`, and `const`**

- **`var`**: Function-scoped, hoisted, can be re-declared.
- **`let`**: Block-scoped, not hoisted (in the same way), cannot be re-declared.
- **`const`**: Block-scoped, not hoisted, must be initialized at the time of declaration, cannot be re-assigned.

### 40. **Differences between `Promise.all()`, `allSettled()`, `any()`, `race()`**

- **`Promise.all()`**: Resolves when all promises are resolved or rejects if any promise is rejected.
- **`Promise.allSettled()`**: Resolves when all promises are settled (resolved or rejected).
- **`Promise.any()`**: Resolves with the first fulfilled promise or rejects if all promises are rejected.
- **`Promise.race()`**: Resolves or rejects as soon as one of the promises resolves or rejects.

### 41. **Limitations of Arrow Functions**

- Cannot be used as constructors.
- No `arguments` object.
- Cannot use `new.target`.
- No `this` or `super` keyword binding.

### 42. **Difference between `find()` and `findIndex()`**

- **`find()`**: Returns the value of the first element in the array that satisfies the provided testing function.
    
    ```jsx
    const arr = [1, 2, 3];
    const result = arr.find(n => n > 1);
    console.log(result); // Output: 2
    
    ```
    
- **`findIndex()`**: Returns the index of the first element in the array that satisfies the provided testing function.
    
    ```jsx
    const index = arr.findIndex(n => n > 1);
    console.log(index); // Output: 1
    
    ```
    

### 43. **What is Tree Shaking in JavaScript?**

- A technique used in JavaScript to eliminate dead code during the bundling process, making the final bundle smaller.

### 44. **Difference between Local

Storage and Cookies**

- **`LocalStorage`**: Stores data with no expiration time, accessible only within the domain that stored it.
- **`Cookies`**: Data stored with an expiration date, accessible within the domain, sent with every HTTP request.

### 45. **Difference between Arrow Function and Regular Function**

- **Arrow Function**:
    - Lexically binds `this`.
    - Cannot be used as a constructor.
    
    ```jsx
    const add = (a, b) => a + b;
    
    ```
    
- **Regular Function**:
    - Dynamic `this`.
    - Can be used as a constructor.
    
    ```jsx
    function add(a, b) {
        return a + b;
    }
    
    ```
    

### 46. **What is a Polyfill in JavaScript?**

- Code that implements a feature on web browsers that do not support the feature natively.
    
    ```jsx
    if (!Array.prototype.includes) {
        Array.prototype.includes = function(search) {
            return this.indexOf(search) !== -1;
        };
    }
    
    ```
    

### 47. **What is a Web Worker?**

- A feature in JavaScript that allows running scripts in background threads, enabling parallel processing without blocking the main thread.

### 48. **What is JSON?**

- **JSON (JavaScript Object Notation)**: A lightweight data interchange format that is easy for humans to read and write and easy for machines to parse and generate.
    
    ```jsx
    const jsonString = JSON.stringify({name: 'John', age: 30});
    const jsonObject = JSON.parse(jsonString);
    
    ```
    

### 49. **What is a Template Literal?**

- String literals allowing embedded expressions, multiple lines, and enhanced string interpolation.
    
    ```jsx
    const name = 'John';
    console.log(`Hello, ${name}!`); // Output: Hello, John!
    
    ```
    

### 50. **What is Event Bubbling?**

- An event propagation method where the event starts from the innermost element and propagates to the outer elements.
    
    ```jsx
    document.getElementById('child').addEventListener('click', function() {
        console.log('Child clicked');
    });
    document.getElementById('parent').addEventListener('click', function() {
        console.log('Parent clicked');
    });
    
    ```
    

### 51. **Difference between `call()` and `apply()`**

- **`call()`**: Invokes a function with a given `this` value and arguments provided one by one.
    
    ```jsx
    function greet(name) {
        console.log('Hello ' + name);
    }
    greet.call(this, 'John');
    
    ```
    
- **`apply()`**: Invokes a function with a given `this` value and arguments provided as an array.
    
    ```jsx
    greet.apply(this, ['John']);
    
    ```
    

### 52. **What is Event Loop in JavaScript?**

- A mechanism that handles the execution of multiple pieces of code by managing the Call Stack and the Callback Queue.
    
    ```jsx
    console.log('Start');
    setTimeout(() => console.log('Timeout'), 0);
    console.log('End');
    // Output: Start, End, Timeout
    
    ```
    

### 53. **What is Function Composition?**

- The process of combining two or more functions to produce a new function.
    
    ```jsx
    const add = x => x + 1;
    const multiply = x => x * 2;
    const composed = x => add(multiply(x));
    console.log(composed(5)); // Output: 11
    
    ```
    

### 54. **Difference between DOMContentLoaded and load Events**

- **`DOMContentLoaded`**: Fired when the initial HTML document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading.
- **`load`**: Fired when the entire page is fully loaded, including all dependent resources.

### 55. **What is Promise Chaining?**

- The process of executing multiple asynchronous operations in sequence, where each operation is chained to the previous one using `.then()`.

### 56. **What is Event Delegation?**

- A technique of handling events by attaching a single event listener to a parent element, and then managing the events for its children using event bubbling.

### 57. **What is Temporal Dead Zone (TDZ)?**

- The period between the entering of a block scope and the actual declaration of a variable during which the variable cannot be accessed.

### 58. **What is a Virtual DOM?**

- An in-memory representation of the real DOM elements that React uses to optimize updates and rendering.

### 59. **How to Optimize a React App?**

- Use memoization techniques (`useMemo`, `React.memo`).
- Optimize component rendering (pure components).
- Lazy loading components.
- Code splitting using Webpack.
- Reduce the number of renders.
- Implement efficient data fetching.

### 60. **What is Type Coercion in JavaScript?**

- The automatic or implicit conversion of values from one data type to another.
    
    ```jsx
    console.log('5' - 1); // Output: 4 (string '5' is converted to number 5)
    
    ```
    

---

A **Promise** in JavaScript is an object representing the eventual completion or failure of an asynchronous operation. It acts as a placeholder for a future value that we don't yet have but expect to receive at some point. Promises help in managing asynchronous code by providing more readable and maintainable ways to handle success, failure, or any other state that an async operation might enter.

### Why Promises Are Needed

Before promises, JavaScript relied heavily on **callbacks** to handle asynchronous tasks, such as network requests or reading files. Callbacks had limitations, including:

- **Callback Hell**: When multiple asynchronous operations were nested inside one another, the code became deeply indented and hard to read and maintain.
- **Error Handling**: Managing errors across multiple asynchronous steps was complex and often inconsistent.
- **Inversion of Control**: When passing a callback function, control over when and how that function executes is lost.

Promises solve these issues by allowing:

- **Chaining**: Promises can be chained, making asynchronous code more linear and easier to read.
- **Better Error Handling**: Errors can be caught in a single `.catch()` block at the end of a promise chain, instead of dealing with multiple error callbacks.

### Key Differences Between Promises and Callbacks

| Aspect | Callbacks | Promises |
| --- | --- | --- |
| Readability | Leads to "callback hell" in nested async operations | More readable, especially with chaining |
| Error Handling | Each callback must handle its own errors | Errors propagate and can be caught in one place |
| Control Flow | Inversion of control, as we rely on the callback owner to invoke it | Developer retains control over the promise |
| Composition | Hard to compose multiple async tasks | Easier to compose with `.then()` and `.catch()` chaining |

### Types of Promises and Their Use Cases

1. **Basic Promise (Pending, Fulfilled, Rejected)**
    - **Description**: A promise starts in a `pending` state, then transitions to `fulfilled` (resolved) if the operation completes successfully, or to `rejected` if it fails.
    - **Use Case**: Used for handling any single asynchronous operation, such as fetching data from an API.
    - **Example**:
        
        ```jsx
        let promise = new Promise((resolve, reject) => {
          setTimeout(() => resolve("Success!"), 1000);
        });
        promise.then((result) => console.log(result)); // Output after 1s: Success!
        
        ```
        
2. **Promise.all()**
    - **Description**: Takes an array of promises and returns a new promise that resolves when all of the input promises resolve or rejects if any promise rejects.
    - **Use Case**: When you want to run multiple asynchronous operations in parallel and proceed only after all of them have completed.
    - **Example**:
        
        ```jsx
        let promise1 = Promise.resolve(3);
        let promise2 = new Promise((resolve) => setTimeout(resolve, 100, "foo"));
        Promise.all([promise1, promise2]).then((values) => console.log(values)); // Output: [3, "foo"]
        
        ```
        
3. **Promise.race()**
    - **Description**: Takes an array of promises and returns a new promise that resolves or rejects as soon as one of the input promises resolves or rejects.
    - **Use Case**: Useful when you want the result of the fastest promise, like making multiple API calls to different endpoints and using whichever responds first.
    - **Example**:
        
        ```jsx
        let promise1 = new Promise((resolve) => setTimeout(resolve, 500, "First"));
        let promise2 = new Promise((resolve) => setTimeout(resolve, 100, "Second"));
        Promise.race([promise1, promise2]).then((value) => console.log(value)); // Output: "Second"
        
        ```
        
4. **Promise.allSettled()**
    - **Description**: Takes an array of promises and returns a new promise that resolves once all input promises have settled, regardless of whether they resolved or rejected.
    - **Use Case**: Useful when you want the results of all promises, but don't want a single rejection to short-circuit the operation.
    - **Example**:
        
        ```jsx
        let promise1 = Promise.resolve(3);
        let promise2 = Promise.reject("Error occurred");
        let promise3 = new Promise((resolve) => setTimeout(resolve, 100, "Done"));
        
        Promise.allSettled([promise1, promise2, promise3]).then((results) => {
          results.forEach((result) => console.log(result));
        });
        // Output:
        // {status: "fulfilled", value: 3}
        // {status: "rejected", reason: "Error occurred"}
        // {status: "fulfilled", value: "Done"}
        
        ```
        
5. **Promise.any()**
    - **Description**: Takes an array of promises and returns a new promise that resolves as soon as any of the input promises resolves. If all of the input promises reject, it rejects with an `AggregateError`.
    - **Use Case**: When you want any successful outcome from a set of promises and can ignore rejections, useful for scenarios like fallback mechanisms.
    - **Example**:
        
        ```jsx
        let promise1 = Promise.reject("Failed");
        let promise2 = new Promise((resolve) => setTimeout(resolve, 200, "First Success"));
        let promise3 = new Promise((resolve) => setTimeout(resolve, 100, "Second Success"));
        
        Promise.any([promise1, promise2, promise3]).then((value) => console.log(value)); // Output: "Second Success"
        
        ```
        

### Summary

Promises provide a cleaner, more manageable way to handle asynchronous operations, avoiding the nested structure of callbacks and enabling better error handling and control flow.