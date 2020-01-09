# Front-end Job Interview Questions and Answers

This file contains a number of front-end interview questions from [the original
repository](https://github.com/h5bp/Front-end-Developer-Interview-Questions)
and answers [I](https://github.com/utatti) answered.

## About contribution

This repository is not to make the answers complete with people. This is to fill my personal answers to the original questions. Therefore, I am afraid I do not merge others' answers, and any PR concerning it will be silently closed.

The questions and some of its contents are from
[the original repository](https://github.com/h5bp/Front-end-Developer-Interview-Questions).
If interested in getting involved, it would be the right place.

## Table of Contents

  1. **[General Questions](#general-questions)** - *[Answers](answers/general-questions.md)*
  1. **[HTML Questions](#html-questions)** - *[Answers](answers/html-questions.md)*
  1. **[CSS Questions](#css-questions)** - *[Answers](answers/css-questions.md)*
  1. **[SASS Questions](#sass-questions)** - *[Answers](answers/sass-questions.md)*
  1. **[JS Questions](#js-questions)** - *[Answers](answers/js-questions.md)*
  1. **[JQUERY Questions](#jquery-questions)** - *[Answers](answers/jquery-questions.md)*
  1. **[Testing Questions](#testing-questions)** - *[Answers](answers/testing-questions.md)*
  1. **[Performance Questions](#performance-questions)** - *[Answers](answers/performance-questions.md)*
  1. **[Network Questions](#network-questions)** - *[Answers](answers/network-questions.md)*
  1. **[Coding Questions](#coding-questions)** - *[Answers](answers/coding-questions.md)*
  1. **[Fun Questions](#fun-questions)** - *[Answers](answers/fun-questions.md)*
  1. **[React Questions](#react-questions)** - *[Answers](answers/ReactJS.md)*
  1. **[Computer Science Questions](#computer-science-questions)** - *[Answers](answers/computer-science.md)*
  1. **[Node Questions](#node-questions)** - *[Answers](answers/node-questions.md)*
  

#### General Questions:

* What did you learn yesterday/this week?
* What excites or interests you about coding?
* What is a recent technical challenge you experienced and how did you solve it?
* What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?
* Talk about your preferred development environment.
* Which version control systems are you familiar with?
* Can you describe your workflow when you create a web page?
* If you have 5 different stylesheets, how would you best integrate them into the site?
* Can you describe the difference between progressive enhancement and graceful degradation?
* How would you optimize a website's assets/resources?
* How many resources will a browser download from a given domain at a time?
  * What are the exceptions?
* Name 3 ways to decrease page load (perceived or actual load time).
* If you jumped on a project and they used tabs and you used spaces, what would you do?
* Describe how you would create a simple slideshow page.
* If you could master one technology this year, what would it be?
* Explain the importance of standards and standards bodies.
* What is Flash of Unstyled Content? How do you avoid FOUC?
* Explain what ARIA and screenreaders are, and how to make a website accessible.
* Explain some of the pros and cons for CSS animations versus JavaScript animations.
* What does CORS stand for and what issue does it address?
* What do you know about design patterns and which one is your favourite?

#### HTML Questions:

* What does a `doctype` do?
* What's the difference between standards mode and quirks mode?
* What's the difference between HTML and XHTML?
* Are there any problems with serving pages as `application/xhtml+xml`?
* How do you serve a page with content in multiple languages?
* What kind of things must you be wary of when design or developing for multilingual sites?
* What are `data-` attributes good for?
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
* What is progressive rendering?
* Have you used different HTML templating languages before?
* What is Semantic HTML?
* What is the Pros and Cons of each: putting script in head - putting script in end of body tag - using Async - using Defer ?

#### CSS Questions:

* What is reflow?What causes reflow?How could you reduce reflow?
* What is Repaints?
* What is the difference between visibility:hidden and display:none?
* How do you clear float?  
* What is the difference between classes and ID's in CSS?
* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
* Describe Floats and how they work.
* Describe z-index and how stacking context is formed.
* Describe BFC(Block Formatting Context) and how it works.
* What are the various clearing techniques and which is appropriate for what context?
* Explain CSS sprites, and how you would implement them on a page or site.
* What are your favourite image replacement techniques and which do you use when?
* How would you approach fixing browser-specific styling issues?
* How do you serve your pages for feature-constrained browsers?
  * What techniques/processes do you use?
* What are the different ways to visually hide content (and make it available only for screen readers)?
* Have you ever used a grid system, and if so, what do you prefer?
* Have you used or implemented media queries or mobile specific layouts/CSS?
* Are you familiar with styling SVG?
* How do you optimize your webpages for print?
* What are some of the "gotchas" for writing efficient CSS?
* What are the advantages/disadvantages of using CSS preprocessors?
  * Describe what you like and dislike about the CSS preprocessors you have used.
* How would you implement a web design comp that uses non-standard fonts?
* Explain how a browser determines what elements match a CSS selector.
* Describe pseudo-elements and discuss what they are used for. 
* Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
* What does ```* { box-sizing: border-box; }``` do? What are its advantages?
* List as many values for the display property that you can remember.
* What's the difference between inline and inline-block?
* What's the difference between a relative, fixed, absolute and statically positioned element?
* The 'C' in CSS stands for Cascading.  How is priority determined in assigning styles (a few examples)?  How can you use this system to your advantage?
* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
* Have you played around with the new CSS Flexbox or Grid specs?
* How is responsive design different from adaptive design?
* Have you ever worked with retina graphics? If so, when and what techniques did you use?
* Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?
* What does 'Pixel Perfect' mean?
* How to deliver responsive images across multiple devices.

#### SASS Questions:
* How to define color variable in SASS?
* How to use mixins in SASS?
#### JS Questions:
* Explain why the treatment of non-dense arrays important or not important in utility libraries.
* Explain the performance impact of deploying ES6 code, compiled to ES5, in all browsers. Explain some gotchas of deploying     ES5. Also explain some gotchas of deploying ES6.
* Explain event delegation
* Explain how `this` works in JavaScript
* Explain how prototypal inheritance works
* What do you think of AMD vs CommonJS?
* Explain why the following doesn't work as an IIFE: `function foo(){ }();`.
  * What needs to be changed to properly make it an IIFE?
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  * How would you go about checking for any of these states?
* What is a closure, and how/why would you use one?
* What's a typical use case for anonymous functions?
* How do you organize your code? (module pattern, classical inheritance?)
* What's the difference between host objects and native objects?
* Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
* What's the difference between `.call` and `.apply`?
* Explain `Function.prototype.bind`.
* When would you use `document.write()`?
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain AJAX in as much detail as possible.
* Explain how JSONP works (and how it's not really AJAX).
* Have you ever used JavaScript templating?
  * If so, what libraries have you used?
* Explain "hoisting".
* Describe event bubbling, and mention how to stop it.
* What's the difference between an "attribute" and a "property"?
* Why is extending built-in JavaScript objects not a good idea?
* Difference between document load event and document ready event?
* What is the difference between `==` and `===`?
* Explain the same-origin policy with regards to JavaScript.
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* Why is it called a Ternary expression, what does the word "Ternary" indicate?
* What is `"use strict";`? what are the advantages and disadvantages to using it?
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
* Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
* Explain what a single page app is and how to make one SEO-friendly.
* What is the extent of your experience with Promises and/or their polyfills?
* What are the pros and cons of using Promises instead of callbacks?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* What language constructions do you use for iterating over object properties and array items?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What is event loop?
  * What is the difference between call stack and task queue?
* What does unobtrusive mean in JavaScript?
* When should you use classical inheritance?
* What is Recursion ?
* What is the difference between undeclared and undefined ?
* What is a constructor call ?
* What is [[Prototype]] and where does it come from ?
* How does [[Prototype]] affect the behaviour of an object ?
* How do we find out where an object's [[Prototype]] points to (3 ways) ?
* How is JavaScript's [[Prototype]] chain not like traditional/classical inheritance ?
* What does [[Prototype]] "delegation" mean and how does it describe object linking in JS ?
* What are the benefits of the "behavior delegation" design pattern ? What are the tradeoffs of using [[Prototype]]?
* What is Coercion ?
* What are the Falsy values in JavaScript ?
* What is the diffrence between == & ===, and what about the performance ?
* What is the difference between a pure function & impure function?
* What is composition in functional programming? 
* What is a Thunk?
* What is the difference between var, let and const in Javascript?
* What is the difference between Promises and async-await?

#### JQUERY Questions:
* Describe event delegation in jQuery. 

#### Testing Questions:

* What are some advantages/disadvantages to testing your code?
* What tools would you use to test your code's functionality?
* What is the difference between a unit test and a functional/integration test?
* What is the purpose of a code style linting tool?

#### Performance Questions:

* What tools would you use to find a performance bug in your code?
* What are some ways you may improve your website's scrolling performance?
* Explain the difference between layout, painting and compositing.

#### Network Questions:

* What is the difference between HTTP protocol and TCP protocol?
* Traditionally, why has it been better to serve site assets from multiple domains?
* Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.
* What are the differences between Long-Polling, Websockets and Server-Sent Events?
* Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
* What are HTTP actions? List all HTTP actions that you know, and explain them.

#### Coding Questions:

*Question: What is the value of `foo`?*
```javascript
var foo = 10 + '20';
```
*Question: What is the value of `foo`?*
```javascript
var foo = 20 + 10 + '30';
```

*Question: If we execute this Javascript, what will the browser's console show??*
```
var text = 'outside';
function logIt(){
console.log(text);
var text = 'inside';
};
logIt();
```

*Question: How would you make this work?*
```javascript
add(2, 5); // 7
add(2)(5); // 7
```
*Question: How would you make this work?*
```javascript
sum(3, 5, 7); // 15
sum(3)(5)(7); // 15
```

*Question: Write a sum() function that accepts any number of arguments and returns their sum.*


*Question: What value is returned from the following statement?*
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```

*Question: The syntax is just fine—the problem is some unexpected behavior, What is it ?*
```
<button id="btn-0">Button 1!</button>
<button id="btn-1">Button 2!</button>
<button id="btn-2">Button 3!</button>
<script type="text/javascript">
  var prizes = ['A Unicorn!', 'A Hug!', 'Fresh Laundry!'];
   for (var btnNum = 0; btnNum < prizes.length; btnNum++) {
      // for each of our buttons, when the user clicks it...
      document.getElementById('btn-' + btnNum).onclick = function() {
        // tell her what she's won!
        alert(prizes[btnNum]);
      };
    }
</script>

```
*Question: What is the value of `window.foo`?*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*Question: What is the outcome of the two alerts below?*
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

*Question: What is the value of `foo.length`?*
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

*Question: What is the value of `foo.x`?*
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```

*Question: What does the following code print?*
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
console.log('three');
```

*Question: What is a potential pitfall with using typeof ```bar === "object"``` to determine if bar is an object? How can this pitfall be avoided?*

*Question: What will the code below output to the console and why?*

```
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```

*Question: What will the code below output to the console and why?*

```
var myObject = {
    foo: "bar",
    func: function() {
        var self = this;
        console.log("outer func:  this.foo = " + this.foo);
        console.log("outer func:  self.foo = " + self.foo);
        (function() {
            console.log("inner func:  this.foo = " + this.foo);
            console.log("inner func:  self.foo = " + self.foo);
        }());
    }
};
myObject.func();
```

*Question: What is the significance of, and reason for, wrapping the entire content of a JavaScript source file in a function block?*



*Question: What is the significance, and what are the benefits, of including 'use strict' at the beginning of a JavaScript source file?*


*Question: Consider the two functions below. Will they both return the same thing? Why or why not?*

```
function foo1()
{
  return {
      bar: "hello"
  };
}

function foo2()
{
  return
  {
      bar: "hello"
  };
}
```



*Question: What is NaN? What is its type? How can you reliably test if a value is equal to NaN?*


*Question: What will the code below output? Explain your answer.*

```
console.log(0.1 + 0.2);
console.log(0.1 + 0.2 == 0.3);
```


*Question: Discuss possible ways to write a function isInteger(x) that determines if x is an integer.*


*Question: In what order will the numbers 1-4 be logged to the console when the code below is executed? Why?*

```
(function() {
    console.log(1); 
    setTimeout(function(){console.log(2)}, 1000); 
    setTimeout(function(){console.log(3)}, 0); 
    console.log(4);
})();
```


*Question: Write a simple function (less than 160 characters) that returns a boolean indicating whether or not a string is a palindrome.*



*Question: Write a ```sum``` method which will work properly when invoked using either syntax below.*

```
console.log(sum(2,3));   // Outputs 5
console.log(sum(2)(3));  // Outputs 5
```


*Question: Consider the following code snippet:*

```
for (var i = 0; i < 5; i++) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  btn.addEventListener('click', function(){ console.log(i); });
  document.body.appendChild(btn);
}
```
(a) What gets logged to the console when the user clicks on “Button 4” and why?

(b) Provide one or more alternate implementations that will work as expected.



*Question: Assuming ```d``` is an “empty” object in scope, say:*

```
var d = {};
```

…what is accomplished using the following code?

```
[ 'zebra', 'horse' ].forEach(function(k) {
	d[k] = undefined;
});
```


*Question: What will the code below output to the console and why?*

```
var arr1 = "john".split('');
var arr2 = arr1.reverse();
var arr3 = "jones".split('');
arr2.push(arr3);
console.log("array 1: length=" + arr1.length + " last=" + arr1.slice(-1));
console.log("array 2: length=" + arr2.length + " last=" + arr2.slice(-1));
```



*Question: What will the code below output to the console and why ?*


```
console.log(1 +  "2" + "2");
console.log(1 +  +"2" + "2");
console.log(1 +  -"1" + "2");
console.log(+"1" +  "1" + "2");
console.log( "A" - "B" + "2");
console.log( "A" - "B" + 2);
```



*Question: The following recursive code will cause a stack overflow if the array list is too large. How can you fix this and still retain the recursive pattern?*

```
var list = readHugeList();

var nextListItem = function() {
    var item = list.pop();

    if (item) {
        // process the list item...
        nextListItem();
    }
};
```


*Question: What is a “closure” in JavaScript? Provide an example.*


*Question: What will be the output of the following code:*

```
for (var i = 0; i < 5; i++) {
	setTimeout(function() { console.log(i); }, i * 1000 );
}
```

Explain your answer. How could the use of closures help here?




*Question: What would the following lines of code output to the console?*

```
console.log("0 || 1 = "+(0 || 1));
console.log("1 || 2 = "+(1 || 2));
console.log("0 && 1 = "+(0 && 1));
console.log("1 && 2 = "+(1 && 2));
```

Explain your answer.



*Question: What will be the output when the following code is executed? Explain.*

```
console.log(false == '0')
console.log(false === '0')
```


*Question: What is the output out of the following code? Explain your answer.*

```
var a={},
    b={key:'b'},
    c={key:'c'};

a[b]=123;
a[c]=456;

console.log(a[b]);
```


*Question: What will the following code output to the console:*

```
console.log((function f(n){return ((n > 1) ? n * f(n-1) : n)})(10));
```

Explain your answer.



*Question: Consider the code snippet below. What will the console output be and why?*


```
(function(x) {
    return (function(y) {
        console.log(x);
    })(2)
})(1);
```



*Question: What will the following code output to the console and why:*

```
var hero = {
    _name: 'John Doe',
    getSecretIdentity: function (){
        return this._name;
    }
};

var stoleSecretIdentity = hero.getSecretIdentity;

console.log(stoleSecretIdentity());
console.log(hero.getSecretIdentity());
```

What is the issue with this code and how can it be fixed.



*Question: Create a function that, given a DOM Element on the page, will visit the element itself and all of its descendents (not just its immediate children). For each element visited, the function should pass that element to a provided callback function.

The arguments to the function should be:

a DOM element
a callback function (that takes a DOM element as its argument)*





*Question: Testing your this knowledge in JavaScript: What is the output of the following code?*

```
var length = 10;
function fn() {
	console.log(this.length);
}

var obj = {
  length: 5,
  method: function(fn) {
    fn();
    arguments[0]();
  }
};

obj.method(fn, 1);
```


*Question: Consider the following code. What will the output be, and why?*

```
(function () {
    try {
        throw new Error();
    } catch (x) {
        var x = 1, y = 2;
        console.log(x);
    }
    console.log(x);
    console.log(y);
})();
```


*Question: What will be the output of this code?*

```
var x = 21;
var girl = function () {
    console.log(x);
    var x = 20;
};
girl ();
```



*Question: How do you clone an object?*




*Question: What will this code print?*

```
for (let i = 0; i < 5; i++) {
  setTimeout(function() { console.log(i); }, i * 1000 );
}
```


*Question: What do the following lines output, and why?*

```
console.log(1 < 2 < 3);
console.log(3 > 2 > 1);
```


*Question: How do you add an element at the begining of an array? How do you add one at the end?*



*Question: Imagine you have this code:?*


```
var a = [1, 2, 3];
```

a) Will this result in a crash?


```
a[10] = 99;
```

b) What will this output?


```
console.log(a[6]);
```


*Question: What is the value of typeof undefined == typeof NULL?*




*Question: What would following code return?*


```
console.log(typeof typeof 1);
```



*Question: What will the following code output and why?*


```
var b = 1;
function outer(){
   	var b = 2
    function inner(){
        b++;
        var b = 3;
        console.log(b)
    }
    inner();
}
outer();
```




#### Fun Questions:

* What's a cool project that you've recently worked on?
* What are some things you like about the developer tools you use?
* Do you have any pet projects? What kind?
* What's your favorite feature of Internet Explorer?
* How do you like your coffee?

#### React Questions:

* Explain the upsides and tradeoffs of using the DllPlugin as opposed to CommonChunksPlugin.
* Virtual DOM vs. Shadow DOM, are they the same thing?
* What is the diffrence between Controlled Component & Uncontrolled Component ?


#### Computer Science Questions:

* What is Runtime Complexity ?
* How can you identify runtime complexity?
* What is Big 'O' Notation ?
* What is Space Complexity ?

#### Node Questions: 

* What is Express.js.
* What is middleware.

## License

[MIT](LICENSE.md)
