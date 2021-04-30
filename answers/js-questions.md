# JS Questions

#### Explain why the treatment of non-dense arrays important or not important in utility libraries.
In general, arrays in JavaScript are sparse – they can have holes in them, because an array is simply a map from indices to values.

eg: ```[ , ,  ]```

In practice, creating a dense array will make your code difficult to understand for others. It is thus better to use utility functions such as _.range (Underscore.range)

http://2ality.com/2012/06/dense-arrays.html

#### Explain the performance impact of deploying ES6 code, compiled to ES5, in all browsers. Explain some gotchas of deploying ES5. Also explain some gotchas of deploying ES6.

Performance impact of deploying ES6 code, compiled to ES5 is that you’re making your code unnecessarily big and slow to support a minority of the users who will probably upgrade their system by the time you manage to configure your Webpack and Babel! 

Deploying ES6 compiled to ES5 Pros:
- You’re using React JSX.
- You want to try the latest features of the language.
- You’re using TypeScript.
- You wanna reduce code size using tree shaking.

Deploying ES6 compiled to ES5 Cons:
- You’re making your code unnecessarily big and slow to support a minority of the users who will probably upgrade their system by the time you manage to configure your Webpack and Babel!

Deploying ES5 Pros:
- ES5 code is smaller. 
- ES5 is almost always faster than ES6, transpiled or otherwise.
- Some features need a polyfill.
- Depending on the size of your codebase and your build process, transpilation may be slow.

Deploying ES5 Cons:
- Not using the latest features of the language.

https://medium.freecodecamp.org/you-might-not-need-to-transpile-your-javascript-4d5e0a438ca


#### Explain event delegation

When an event is fired from an element, the event will be bubbled up to its
parent nodes. However, the original element where the event occurs, called
'target', stays the same in the event object. Using the `target` property, we
can always keep tracking which element actually causes an event captured by
its parent, and it can help use reduce the number of event handlers as we
sometimes don't need to add event listeners for every element (requires much
less memory).


#### Explain how `this` works in JavaScript

'this' in JavaScript refers to the object that is executing the function.

1 - If the function is a method in an object, 'this' refers to the Object itself.

2 - If the function is not part of an object, 'this' refers to the window in browsers and global in node.

3 - If the new operator used on normal function, it will create new empty object and set 'this' to the empty object.

A function's this keyword behaves a little differently in JavaScript compared to other languages. It also has some differences between strict mode and non-strict mode.

In most cases, the value of this is determined by how a function is called. It can't be set by assignment during execution, and it may be different each time the function is called. ES5 introduced the bind method to set the value of a function's this regardless of how it's called, and ES2015 introduced arrow functions which don't provide their own this binding (it retains the this value of the enclosing lexical context).

https://www.youtube.com/watch?v=gvicrj31JOM

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this

#### Explain how prototypal inheritance works

*Objects are built by constructor calls (function with a new key word) not by constructors, In class based languages (like Java or C++) prototypal inheritance is a copy relationship (If my son lose a leg I won't lose a leg too), In JS prototypal inheritance is a link relationship (If my son lose a leg I lose a leg too)*

JavaScript is a bit confusing for developers experienced in class-based languages (like Java or C++), as it is dynamic and does not provide a class implementation per se (the class keyword is introduced in ES2015, but is syntactical sugar, JavaScript remains prototype-based).

When it comes to inheritance, JavaScript only has one construct: objects. Each object has a private property which holds a link to another object called its prototype. That prototype object has a prototype of its own, and so on until an object is reached with null as its prototype. By definition, null has no prototype, and acts as the final link in this prototype chain.

Nearly all objects in JavaScript are instances of Object which sits on the top of a prototype chain.

While this confusion is often considered to be one of JavaScript's weaknesses, the prototypal inheritance model itself is, in fact, more powerful than the classic model. It is, for example, fairly trivial to build a classic model on top of a prototypal model.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9

#### What do you think of AMD vs CommonJS?

CommonJS using the keywords require and exports. require is a function used to import functions from another module. exports is an object where any function put into it will get exported. NodeJS implementation They are heavily influenced by CommonJS specification. The major difference arises in the exports object. NodeJS modules use module.exports as the object to get exported while CommonJS uses just the exports variable.


AMD (Asynchronous Module Definition) was born as CommonJS wasn’t suited for the browsers early on. As the name implies, it supports asynchronous module loading. The function is called only when the requested modules are finished loading. The define function takes the first argument as an array of dependency modules. These modules are loaded in a non-blocking manner in the background and once the loading is completed, the callback function is executed.


https://auth0.com/blog/javascript-module-systems-showdown/


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

i.e:

Function Expressions (Anonymous Function), not hoisted and more flexible.

Function Declaration (Named Function), hoisted and Easy debugging.

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

#### Describe event bubbling, and mention how to stop it.

It's when an event is bubbled into container elements, in the higher level of a
DOM tree.

We can stop it using ```event.stopPropagation();```

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

```

for (var i=1; i < 101; i++){
    if (i % 15 == 0) console.log("FizzBuzz");
    else if (i % 3 == 0) console.log("Fizz");
    else if (i % 5 == 0) console.log("Buzz");
    else console.log(i);
}

```

https://codeburst.io/javascript-breaking-down-the-shortest-possible-fizzbuzz-answer-94a0ad9d128a

https://ditam.github.io/posts/fizzbuzz/

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

Mutable objects are objects that can be modified after it has been created, unmutable objects are objects that can not be modified after it has been created

https://medium.com/@ibraheemabukaff/mutability-immutability-in-javascript-48022d660015

#### What is an example of an immutable object in JavaScript?

```
let a = {foo: "bar"};
let b = Object.assign({},a);
b.foo = "bar2"
console.log(a); // {foo: "bar"}
console.log(b);// {foo: "bar2"}
console.log(b === a) // false
```

To change only the object `b` ,we assigned it to` Object.assign({},a)`. by this way we kept the object `a` in the original state and the object `b` can changed according to our needs without affecting object `a` .

#### What are the pros and cons of immutability?

Immutability has several advantages, including (but not limited to):

Programs with immutable objects are less complicated to think about, since you don't need to worry about how an object may evolve over time.

You don't need to make defensive copies of immutable objects when returning or passing to other functions, since there is no possibility an immutable object will be modified behind your back.

One copy of an object is just as good as another, so you can cache objects or re-use the same object multiple times.
Immutable objects are good for sharing information between threads in a multi-threaded environment since they don't need to be synchronized.

Operations on immutable objects return new immutable objects while operations that cause side-effects on mutable objects usually return void. This means several operations can be chained together. For instance
```("foo" + "bar" + "baz").length()```

In languages where functions are first class values, operations like map, reduce, filter, etc. are basic operations on collections. These can be combined in many ways, and can replace most loops in a program.

There are of course some disadvantages:

Cyclic data structures such as graphs are difficult to build. If you have two objects which can't be modified after initialization, how can you get them to point to each other?

Allocating lots and lots of small objects rather than modifying ones you already have can have a performance impact. Usually the complexity of either the allocator or the garbage collector depends on the number of objects on the heap.

Naive implementations of immutable data structures can result in extremely poor performance. For instance, concatenating many immutable strings (like in Java) is O(n2) when the best algorithm is O(n). It is possible to write efficient immutable data structures, it just takes a little more thought.

https://stackoverflow.com/questions/1863515/pros-cons-of-immutability-vs-mutability


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


https://www.youtube.com/watch?v=jJ6ccR3nF_c&t=247s

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

#### What are the Falsy values in JavaScript ?

- " "
- 0, +0, -0
- null
- NaN
- false
- undefined

#### What is the diffrence between == & ===, and what about the performance ?
== allows coercion and === disallows coercion, unlike the common misconception that == checks value & === checks value and type. == makes more work due to it allows coercion and thus == might be a little slower when the types are different (=== 30% faster). 

- If the types compared are the same, they are identical. That is to say they use the exact same algorithm.
- If the types are different, then performance is irrelevant. Either you need type coercion, or you don't. If you need it, don't use == because the result you get may be unexpected.

#### What is the difference between a pure function & impure function?

A pure function is a function which are sure to provide exact result when the same arguments are passed. For having a function as pure function if must not have any external variable, data store call, ajax request or any other global variables.

This means that you can be completely sure that every time you call the function with the same arguments, you will always get the same result.

Impure function is When function uses any variables not passed in as arguments, the variables used inside functions may cause side effects. Lets say in case of ajax calls it will fail, In such cases the function is called impure function. When a function depends on variables or functions outside of its lexical scope, you can never be sure that the function will behave the same every time it’s called. 

Characteristics of Pure Function:

- The return value of the pure func­tions solely depends on its arguments Hence, if you call the pure functions with the same   set of arguments, you will always get the same return values.

- They do not have any side effects like network or database calls.

- They do not modify the arguments which are passed to them.

Characteristics of Impure functions:

- The return value of the impure functions does not solely depend on its arguments Hence, if you call the impure func­tions     with the same set of arguments, you might get the different return values For example, Math.random(), Date.now().

- They may have any side effects like network or database calls.

- They may modify the arguments which are passed to them.

#### What is composition in functional programming? 

Taking the output of one function and putting it directly in the input of another function, instead of calling one function and then calling another function.


#### What is a Thunk? 
A Thunk is a function that have everything already that need to have (doesn't need to pass arguments) to give an output back once it has been called, It contain closured state that act like a token used in application level. It act as container that we can use anywhere in the application.


#### What is the difference between var, let and const in Javascript?

var: The scope of a variable defined with the keyword “var” is limited to the “function” within which it is defined. If it is defined outside any function, the scope of the variable is global.
var is “function scoped”.

let: The scope of a variable defined with the keyword “let” or “const” is limited to the “block” defined by curly braces i.e. {} .
“let” and “const” are“block scoped”.

const: The scope of a variable defined with the keyword “const” is limited to the block defined by curly braces. However if a variable is defined with keyword const, it cannot be reassigned.
“const” cannot be re-assigned to a new value. However it CAN be mutated.

#### Compare between let and var regarding Scoping rules, Hoisting, Creating global object property & Redeclaration ?

Scoping rules:

Main difference is scoping rules. Variables declared by var keyword are scoped to the immediate function body (hence the function scope) while let variables are scoped to the immediate enclosing block denoted by { } (hence the block scope).

The reason why let keyword was introduced to the language was function scope is confusing and was one of the main sources of bugs in JavaScript.

Hoisting: 

While variables declared with var keyword are hoisted (initialized with undefined before the code is run) which means they are accessible in their enclosing scope even before they are declared:

let variables are not initialized until their definition is evaluated. Accessing them before the initialization results in a ReferenceError. Variable said to be in "temporal dead zone" from the start of the block until the initialization is processed.

Creating global object property:

At the top level, let, unlike var, does not create a property on the global object.

Redeclaration:

In strict mode, var will let you re-declare the same variable in the same scope while let raises a SyntaxError.

https://stackoverflow.com/questions/762011/whats-the-difference-between-using-let-and-var

#### What is the difference between Promises and async-await?

https://www.loginradius.com/blog/async/callback-vs-promises-vs-async-await/

https://medium.com/better-programming/should-i-use-promises-or-async-await-126ab5c98789


#### How to use array destructuring ?

https://www.freecodecamp.org/news/array-and-object-destructuring-in-javascript/


#### What is the difference between event bubbling and event capturing in JavaScript ?

https://medium.com/@vsvaibhav2016/event-bubbling-and-event-capturing-in-javascript-6ff38bec30e


#### What is the difference between value and reference in JavaScript ?

Javascript has 5 data types that are passed by value: Boolean, null, undefined, String, and Number. We’ll call these primitive types. If a primitive type is assigned to a variable, we can think of that variable as containing the primitive value.

Javascript has 3 data types that are passed by reference: Array, Function, and Object. These are all technically Objects, so we’ll refer to them collectively as Objects. Variables that are assigned a non-primitive value are given a reference to that value. That reference points to the object’s location in memory. The variables don’t actually contain the value.

https://codeburst.io/explaining-value-vs-reference-in-javascript-647a975e12a0


#### What is Babel?

Babel is a JavaScript transpiler that converts edge JavaScript into plain old ES5 JavaScript that can run in any browser (even the old ones).

It makes available all the syntactical sugar that was added to JavaScript with the new ES6 specification, including classes, fat arrows and multiline strings.


http://nicholasjohnson.com/blog/what-is-babel/
