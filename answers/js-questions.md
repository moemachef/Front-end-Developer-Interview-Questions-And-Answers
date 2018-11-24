# JS Questions

#### Explain event delegation

When an event is fired from an element, the event will be bubbled up to its
parent nodes. However, the original element where the event occurs, called
'target', stays the same in the event object. Using the `target` property, we
can always keep tracking which element actually causes an event captured by
its parent, and it can help use reduce the number of event handlers as we
sometimes don't need to add event listeners for every element (requires much
less memory).


#### Explain how `this` works in JavaScript
A function's this keyword behaves a little differently in JavaScript compared to other languages. It also has some differences between strict mode and non-strict mode.

In most cases, the value of this is determined by how a function is called. It can't be set by assignment during execution, and it may be different each time the function is called. ES5 introduced the bind method to set the value of a function's this regardless of how it's called, and ES2015 introduced arrow functions which don't provide their own this binding (it retains the this value of the enclosing lexical context).

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this

#### Explain how prototypal inheritance works

JavaScript is a bit confusing for developers experienced in class-based languages (like Java or C++), as it is dynamic and does not provide a class implementation per se (the class keyword is introduced in ES2015, but is syntactical sugar, JavaScript remains prototype-based).

When it comes to inheritance, JavaScript only has one construct: objects. Each object has a private property which holds a link to another object called its prototype. That prototype object has a prototype of its own, and so on until an object is reached with null as its prototype. By definition, null has no prototype, and acts as the final link in this prototype chain.

Nearly all objects in JavaScript are instances of Object which sits on the top of a prototype chain.

While this confusion is often considered to be one of JavaScript's weaknesses, the prototypal inheritance model itself is, in fact, more powerful than the classic model. It is, for example, fairly trivial to build a classic model on top of a prototypal model.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9

#### What do you think of AMD vs CommonJS?

CommonJS using the keywords require and exports. require is a function used to import functions from another module. exports is an object where any function put into it will get exported. NodeJS implementation They are heavily influenced by CommonJS specification. The major difference arises in the exports object. NodeJS modules use module.exports as the object to get exported while CommonJS uses just the exports variable.
AMD (Asynchronous Module Definition) was born as CommonJS wasn’t suited for the browsers early on. As the name implies, it supports asynchronous module loading. The function is called only when the requested modules are finished loading. The define function takes the first argument as an array of dependency modules. These modules are loaded in a non-blocking manner in the background and once the loading is completed, the callback function is executed.


#### Explain why the following doesn't work as an IIFE: `function foo(){ }();`.
An IIFE (pronouced as ‘iffy’) is an abbreviation for Immediately Invoked Function Expression. It is a common Javascript design pattern used by popular JS libraries such as jQuery, Backbone.js. Purpose of using an IIFE is to maintain code inside of a local scope. This means, to be able to use global object inside of IIFE, you will need to pass it as arguments.

As for an explanation, the following code doesn’t work as an IIFE because it is a function declaration, it does invoked immediately due to its parenthesis at the end, but there are downsides to using this approach.
```function foo() {}()```;
First, it unnecessarily takes up a name in the global namespace, increasing the possibility of name collisions. Second, the intentions of this code aren’t as self-documenting as an IIFE. And third, because it is named and isn’t self-documenting it might accidentally be invoked more than once.
For the above code to be considered an IIFE, it needs to be an anonymous function, a function without a name, this is because IIFE needs to be Invoked Immediately without invoking it a function name. We also need to wrap the anonymous function with parenthesis, so the Javascript parser treats our anonymous function as a function expression.

```(function() {}());```

#### What needs to be changed to properly make it an IIFE?

```js
(function foo() { })(); // or
(function foo() { }());
```

#### What's the difference between a variable that is: `null`, `undefined` or undeclared? and How would you go about checking for any of these states?

undefined is a variable that has been declared but no value exists and is a type of itself ‘undefined’.


null is a value of a variable and is a type of object.


undeclared variables is a variable that has been declared without ‘var’ keyword.

We use ‘console.log();’ and ‘type of’ to check if a variable is undefined or null.

#### What is a closure, and how/why would you use one?

Closures are inner functions inside of an outer function. They have their own local scope and has access to outer function’s scope, parameters (but NOT arguments object), and they also have access to global variables.


https://medium.com/@rlynjb/js-interview-question-what-is-a-closure-and-how-why-would-you-use-one-b6fd45ea95f6

http://javascriptissexy.com/understand-javascript-closures-with-ease/

#### What's a typical use case for anonymous functions?

Since Anonymous Functions are function expressions rather than the regular function declaration which are statements. Function expressions are more flexible. We can assign functions to variables, object properties, pass them as arguments to other functions, and even write a simple one line code enclosed in an anonymous functions.

#### How do you organize your code? (module pattern, classical inheritance?)

There are several options in implementing Module Pattern. An option I mostly use is Object Literal Notation for encapsulating and organizing my code, but upon further readings, Module Pattern using Anonymous Closures, Global Import, and Module Export have sparked my interest as it provides more features for private and public var/methods. It still uses object literal but as to return values from the scoping function.

#### What's the difference between host objects and native objects?

- Host objects: what an environment(browser, Node.js, etc) provides
- Native objects: what JavaScript provides


#### Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

```function Person() {}```

Function Declaration: Code above declares a function statement (statements perform an action) but does not execute, however, it does get registered into the global namespace.

```var person = Person()```

Function Expression: A variable ‘var person’ has been defined and contains a value reference to a Person function. Any JavaScript Expressions (including Function Expressions) always returns a value. This may also be an Anonymous function if no name has been assign to a function but wrapped in parenthesis to be interpreted as an expression.

```var person = new Person()```

Function Constructor: By adding the keyword ‘new’. We are instantiating a new object of the Person class constructor. A function declaration is just a regular function unless it has been instantiated, it then becomes a class constructor.

#### What's the difference between `.call` and `.apply`?

Invoking a function with .apply and .call allows us to point an object to the invoked function by passing in the object as first argument and second argument (and so on) as its values.
The function’s ‘this’ keyword will be manipulated when invoked with .apply or .call.
From what I understand, .apply and .call are methods we use to assign the ‘this’ keyword from the invoked function to reference to an object for the duration of the method invocation.

Besides passing in an argument to a .call or .apply methods that references to the ‘this’ keyword of an invoked function, we can also pass in a 2nd argument or more. A good mnemonic to explain their differences are:

.Call Counts the number of arguments separated by Comma
.call method accepts one or more arguments as objects and requires to be listed explicitly, means, it is a fixed number of arguments.

.Apply uses Array as an Argument
.apply method requires an array as its 2nd argument. This method is used if you don’t know the number of arguments to be passed or the arguments is already in an array.


https://medium.com/@rlynjb/js-interview-question-what-s-the-difference-between-call-and-apply-84e6c6b84f20

#### Explain `Function.prototype.bind`.

To avoid polluting an outer function’s scope, we can use bind method instead. Once we invoked a function with bind method, it bounds our closure or inner function with the outer function’s scope.

There are other methods of setting the scope of a function. Other two are apply() and call().
Difference between apply() & call() and bind() method is:

Functions invoked with apply() & call() methods gets executed first and of course, we also pass along the function’s scope as well while Functions invoked with bind() method just sets the scope, but doesn’t get executed.

https://medium.com/@rlynjb/js-interview-question-explain-function-prototype-bind-bbdaed41bd89

#### When would you use `document.write()`?

When document.write() is executed after page load, it replaces the entire header and body tag with the given parameter value in string. The only seem appropriate usage for document.write() is when working third parties like Google Analytics and such for including their scripts. This is because document.write() is mostly available in any browser. Since third party companies have no control over the user’s browser dependencies (ex. jQuery), document.write() can be used as a fallback or a default method.

https://medium.com/@rlynjb/js-interview-question-when-would-you-use-document-write-ccc199137715

#### What's the difference between feature detection, feature inference, and using the UA string?

- Feature detection: directly check if a feature is implemented

```js
if (Promise) {
  let a = Promise.resolve('hello');
}
```

- Feature inference: infer if a feature is implemented by checking other properties

```js
if (MozSmsMessage) {
  // guess it must be Firefox...
}
```

- UA string: UA stands for UserAgent, which a browser natively exposes to
  scripts and HTTP header

```js
console.log(navigator.userAgent); // "Mozilla/5.0 (Macintosh; ..."
```

#### Explain AJAX in as much detail as possible.

Simply put, AJAX is the use of JavaScript to send and receive using HTTP without reloading the page. AJAX is an acronym for asynchronous JavaScript and XML, and is used as a technique for creating client-side asynchronous web applications. AJAX is considered a group of technologies. HTML and CSS can be used in combination to mark up and style information. JavaScript and the XMLHttpRequest object provide the method for exchanging data asynchronously between the browser and the server.

AJAX provides more efficient and smoother running applications, which gives users better interactive experiences.

https://medium.com/@morgan_ashley/front-end-developer-interview-question-03-4b8c94a42442

#### Explain how JSONP works (and how it's not really AJAX).


JSONP is a method for sending JSON data without worrying about cross-domain issues.


A JSONP response contains a callback function usually written in JavaScript,
and when the response is flushed, the callback will be launched. It's more like
script tag injection, rather than AJAX.

#### Have you ever used JavaScript templating?

Yes.

#### If so, what libraries have you used?

Handlebars, Mustache, etc.

#### Explain "hoisting".
Declarations are put into memory during the compile mode which means a variable can be used before it has been declared.
In compile mode the value is not stored, only the variable declaration. What is hoisted or stored in memory during compile mode is what goes before the = and not what is after it.
Function expressions are not hoisted and therefore can not be used before they have been defined. Arrow functions are like function expressions and therefore are not hoisted either.

https://medium.com/bluekiri/the-confusion-of-javascript-scope-and-hoisting-3e9c759eb419

#### Describe event bubbling.

It's when an event is bubbled into container elements, in the higher level of a
DOM tree.

#### What's the difference between an "attribute" and a "property"?

- Attribute: specified in HTML, always in the form of string
- Property: specified in DOM object, can have any type of JavaScript

#### Why is extending built-in JavaScript objects not a good idea?

1.JavaScript may implement their own version of your custom method in the future (using the same name) and this will override your custom method.


2.Modifying the behaviour of current built-in JS objects is not a good practice as it breaks its default functionality and it will break your code using that specific built-in JS object method or property.

#### Difference between document load event and document ready event?

- document ready: when a HTML document is loaded and rendered
- document load: when a HTML document and assets in the document are all loaded
  and rendered

#### What is the difference between `==` and `===`?

By using = you assign a value to something.

By using == you check if something is equal to something else. This is not strict

By using === you check if something is equal to something else. This is also strict.

Strict is that it checks not only the equality of the two values, it compares the types of the two values too. Using == will try and convert one side of the expression to be the same type as the other



#### Explain the same-origin policy with regards to JavaScript.

Same-origin means having same host, port and protocol(HTTP or HTTPS). If a
script in the different origin should be accessed, we can consider using CORS.

#### Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```

```js
let duplicate = (arr) => arr.concat(arr);
```

#### Why is it called a Ternary expression, what does the word "Ternary" indicate?

The word “ternary” comes from the n-ary word setup. Other examples of n-ary words are unary and binary. All of these (including ternary) are operands. The prefix section of their name lists how many inputs the operand accepts.

A unary operand accepts one parameter, e.g. -1, where - is the operand, and 1 is the parameter.

A binary operand accepts two parameters, e.g. 2 + 3, where + is the operand, and 2 and 3 are the parameters.

So a ternary operand accepts three parameters.

#### What is `"use strict";`? what are the advantages and disadvantages to using it?

Advantages

- Cannot assign a value to an undefined global variable
- Fire TypeError for not-allowed assignments
- `this` in a normal function refers to `undefined`, instead of `global`

In short, it secures JavaScript.

Disadvantage

- When using global strict mode and concatenating the script with other scripts
  not using strict mode, the other scripts can be broken.

#### Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`

*Not answered yet*

#### Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?

The primary reason why global variables are discouraged in javascript is because, in javascript all code share a single global namespace, also javascript has implied global variables i.e. variables which are not explicitly declared in local scope are automatically added to global namespace. Relying too much on global variables can result in collisions between various scripts on the same page

#### Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?

The load event fires at the end of the document loading process. At this point, all of the objects in the document are in the DOM, and all the images, scripts, links and sub-frames have finished loading. To execute anything post document load, we fire these events. ‘DOMContentLoaded’ or jQuery’s loaded are another options.

#### Explain what a single page app is and how to make one SEO-friendly.

SPA is a web application or web site that fits on a single web page with the goal of providing a more fluid user experience similar to a desktop application. In a SPA, either all necessary code — HTML, JavaScript, and CSS — is retrieved with a single page load, or the appropriate resources are dynamically loaded and added to the page as necessary, usually in response to user actions.

https://stackoverflow.com/questions/20048476/how-to-improve-seo-for-single-page-application

https://cdnjs.com/libraries/backbone.js/tutorials/seo-for-single-page-apps

#### What is the extent of your experience with Promises and/or their polyfills?

The biggest advangtage of Promise is that it solves the problem of callback hell. the biggest disadvantage currently require external library or polyfill to achieve this.

Polyfills:

- jQuery - Deferred
- Bluebird
- Q
- When

#### What are the pros and cons of using Promises instead of callbacks?

pros - solves the problem of callback hell.
cons - currently require external library or polyfill to achieve this.

#### What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

CoffeeScript. Pros/Cons: Syntactic sugar, readable code, and use of good patterns vs debugging and compilation issues.

#### What tools and techniques do you use debugging JavaScript code?

Web/Browser console using console.log. Firebug, Developer Tools, stop points

#### What language constructions do you use for iterating over object properties and array items?

for loop, for..in, for each..in, map, reduce etc.

#### Explain the difference between mutable and immutable objects.
#### What is an example of an immutable object in JavaScript?
#### What are the pros and cons of immutability?
#### How can you achieve immutability in your own code?

Mutable objects are those whose state is allowed to change over time. An immutable value is the exact opposite — after it has been created, it can never change. Strings and Numbers are inherently immutable in javascript.

https://www.sitepoint.com/immutability-javascript/

#### Explain the difference between synchronous and asynchronous functions.

Synchronous: Step wise execution. Next line executed after first. 

Asynchronous: Execution moves to next step before first is finished. 

#### What is event loop?

It is a constantly running process that checks if the call stack is empty. Imagine it like a clock and every time it ticks it looks at the Call Stack and if it is empty it looks into the Event Queue. If there is something in the event queue that is waiting it is moved to the call stack. If not, then nothing happens.

#### What is the difference between call stack and task queue?
1.Call Stack :- It’s a data structure which records the function calls, basically where in the program we are. If we call a function to execute , we push something on to the stack, and when we return from a function, we pop off the top of the stack.

2.Heap :- Objects are allocated in a heap i.e mostly unstructured region of memory. All the memory allocation to variables and objects happens here.

3.Queue :- A JavaScript runtime contains a message queue, which is a list of messages to be processed and the associated callback functions to execute. When the stack has enough capacity, a message is taken out of the queue and processed which consists of calling the associated function (and thus creating an initial stack frame). The message processing ends when the stack becomes empty again. In basic words , these messages are queued in response to external async events(such as a mouse being clicked or receiving the response to an HTTP request), given a callback function has been provided. If, for example a user were to click a button and no callback function was provided — no message would have been enqueued.


#### What does unobtrusive mean in JavaScript?
Unobtrusive is a JavaScript methodology that helps overcome browser inconsistencies through the separation of page functionality and structure.

#### When should you use classical inheritance?
The answer is never or almost never or if all options are exhausted.

#### What is Recursion ?
Recursion in JavaScript is, simply put, the ability to call a function from within itself.

#### What's the difference between undeclared and undefined ?
Undeclared never been declared in any scope, undefined defined but never have a value.


#### What is a constructor call ?
It's a function called with the "new" keyword.

#### What is [[Prototype]] and where does it come from ?
It's a linkage from one object to an other, it's created at the time the object is created.

#### How does [[Prototype]] affect the behaviour of an object ?
It delegate up to the chain.

#### How do we find out where an object's [[Prototype]] points to (3 ways) ?
Dunder proto ```(__proto__)``` , ```Object.getPrototypeOf()``` & ```.constructor.prototype```

#### How is JavaScript's [[Prototype]] chain not like traditional/classical inheritance ?
Insted of copying things down we have live links up the prototype chain.

#### What does [[Prototype]] "delegation" mean and how does it describe object linking in JS ?
The prototype chain is delegation link from one object to an other that allow those objects to share context at call time.

#### What are the benefits of the "behavior delegation" design pattern ? What are the tradeoffs of using [[Prototype]]?
Benefit is independent testability and tradeoffs is that it's more complex.

#### What is Coercion ?
It's the dynamic languages way of expressing how values convert from one type to another.
