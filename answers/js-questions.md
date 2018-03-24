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

###### What needs to be changed to properly make it an IIFE?

```js
(function foo() { })(); // or
(function foo() { }());
```

#### What's the difference between a variable that is: `null`, `undefined` or undeclared?
###### How would you go about checking for any of these states?

*Not answered yet*

#### What is a closure, and how/why would you use one?

*Not answered yet*

#### What's a typical use case for anonymous functions?

*Not answered yet*

#### How do you organize your code? (module pattern, classical inheritance?)

*Not answered yet*

#### What's the difference between host objects and native objects?

- Host objects: what an environment(browser, Node.js, etc) provides
- Native objects: what JavaScript provides


#### Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

*Not answered yet*

#### What's the difference between `.call` and `.apply`?

*Not answered yet*

#### Explain `Function.prototype.bind`.

*Not answered yet*

#### When would you use `document.write()`?

When someone gives me one million dollar for doing it.

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

*Not answered yet*

#### Explain how JSONP works (and how it's not really AJAX).

A JSONP response contains a callback function usually written in JavaScript,
and when the response is flushed, the callback will be launched. It's more like
script tag injection, rather than AJAX.

#### Have you ever used JavaScript templating?

Yes.

###### If so, what libraries have you used?

Handlebars, Mustache, etc.

#### Explain "hoisting".

*Not answered yet*

#### Describe event bubbling.

It's when an event is bubbled into container elements, in the higher level of a
DOM tree.

#### What's the difference between an "attribute" and a "property"?

- Attribute: specified in HTML, always in the form of string
- Property: specified in DOM object, can have any type of JavaScript

#### Why is extending built-in JavaScript objects not a good idea?

*Not answered yet*

#### Difference between document load event and document ready event?

- document ready: when a HTML document is loaded and rendered
- document load: when a HTML document and assets in the document are all loaded
  and rendered

#### What is the difference between `==` and `===`?

*Not answered yet*

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

*Not answered yet*

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

*Not answered yet*

#### Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?

*Not answered yet*

#### Explain what a single page app is and how to make one SEO-friendly.

*Not answered yet*

#### What is the extent of your experience with Promises and/or their polyfills?

*Not answered yet*

#### What are the pros and cons of using Promises instead of callbacks?

*Not answered yet*

#### What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

*Not answered yet*

#### What tools and techniques do you use debugging JavaScript code?

*Not answered yet*

#### What language constructions do you use for iterating over object properties and array items?

*Not answered yet*

#### Explain the difference between mutable and immutable objects.
###### What is an example of an immutable object in JavaScript?
###### What are the pros and cons of immutability?
###### How can you achieve immutability in your own code?

*Not answered yet*

#### Explain the difference between synchronous and asynchronous functions.

*Not answered yet*

#### What is event loop?
###### What is the difference between call stack and task queue?

*Not answered yet*

