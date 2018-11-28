# Coding Questions

#### *Question: What is the value of `foo`?*
```javascript
var foo = 10 + '20';
```

*Answer:* `'1020'`, because of type coercion from Number to String

#### *Question: What is the value of `foo`?*
```javascript
var foo = 20 + 10 + '30';
```
*Answer:* `'3030'`, because of type coercion from Number to String

#### *Question: If we execute this Javascript, what will the browser's console show??*
```
var text = 'outside';
function logIt(){
console.log(text);
var text = 'inside';
};
logIt();
```
*Answer:* Neither outside, nor inside, the result is`undefined`, It’s because JavaScript initialization is not hoisted. (Why doesn’t it show the global value of outside? The reason is that when the function is executed, it checks that there’s a local x variable present but doesn’t yet declare it, so it won’t look for global one.)




#### *Question: How would you make this work?*
```javascript
add(2, 5); // 7
add(2)(5); // 7
```

*Answer:* A general solution for any number of parameters
```js
function add(x, y) {
  if (y !== undefined) {
    return x + y;
  } else {
    return function(y) { return x + y; };
  }
}

add(2, 5); // 7
add(2)(5); // 7
```

#### *Question: How would you make this work?*
```javascript
sum(3, 5, 7); // 15
sum(3)(5)(7); // 15
```
*Answer:* A general solution for any number of parameters
```js
function sum(x, y, z) {
  if (y !== undefined && z !== undefined) {
    return (x + y + z);
  } else {
    return function(y) { 
      return function(z){
        return (x + y + z)
      }
    };
  }
}
```


#### *Question: Write a sum() function that accepts any number of arguments and returns their sum.*
```javascript
function sum() {
    var s = 0;
    for (var i=0; i < arguments.length; i++) {
        s += arguments[i];
    }
    return s;
}
```
#### *Question: What value is returned from the following statement?*
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```

*Answer:* It's actually a reverse method for a string - `'goh angasal a m\'i'`

#### *Question: The syntax is just fine—the problem is some unexpected behavior, What is it ?*
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
*Answer:*
-  The for loop when completed the variable i has a value of 3 each time the loop try to start.

- We can fix it  by using closures with an immediately invoked function expression (IIFE), which creates a closure around our code, capturing the value of i in the IIFE's argument to keep it from changing when the callback is executed.

- We could also have solved the problem using Function#bind to capture the value of i in a new function with that value applied as the first argument.

- We could also replace for loop with forEach method.

- We could also use let insted of var, With the introduction of let and block scoping in ES6, the previously mentioned problem disappears - so long as you declare your for loop initializers using let instead of var. Using let in our loop initializer makes i block scoped to the block of code within the loop. This properly captures the value for our callbacks and keeps us from polluting the global scope with for loop initializers all over the place. Not to mention, it keeps the code more readable and concise - nested IIFE's inside for loops don't really add to code clarity or understanding and can be verbose to type.

https://www.datchley.name/loop-variable-gotcha/

#### *Question: What is the value of `window.foo`?*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*Answer:* Always `'bar'`

The or (||) operator. In an expression of the form X||Y, X is first evaluated and interpreted as a boolean value. If this boolean value is true, then true is returned and Y is not evaluated, since the “or” condition has already been satisfied. If this boolean value is “false”, though, we still don’t know if X||Y is true or false until we evaluate Y, and interpret it as a boolean value as well.

#### *Question: What is the outcome of the two alerts below?*
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

*Answer:*
- First: `Hello World`
- Second: Throws an exception, `ReferenceError: bar is not defined`

#### *Question: What is the value of `foo.length`?*
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

*Answer:* `.push` is mutable - `2`

#### *Question: What is the value of `foo.x`?*
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```

*Answer:* `undefined`. Rather, `bar.x` is `{n: 2}`.

`foo.x = foo = {n: 2}` is the same as `foo.x = (foo = {n: 2})`. It is because
a left term is first referenced and then a right term is evaluated when an
assignment is performed in JavaScript. When `foo.x` is referenced, it refers
to an original object, `{n: 1}`. So, when the result of the right term, `{n:
2}`, is evaluated, it will assigned to the original object, which is at the
moment referenced by `bar`.

#### *Question: What does the following code print?*
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
console.log('three');
```

*Answer:* `one`, `three` and `two`. It's because `console.log('two');` will be
invoked in the next event loop.


#### *Question: What is a potential pitfall with using typeof ```bar === "object"``` to determine if bar is an object? How can this pitfall be avoided?*

*Answer:* 

Although typeof ```bar === "object"``` is a reliable way of checking if ```bar``` is an object, the surprising gotcha in JavaScript is that ```null``` is also considered an object!

Therefore, the following code will, to the surprise of most developers, log ```true``` (not ```false```) to the console:

```
var bar = null;
console.log(typeof bar === "object");  // logs true!
```
As long as one is aware of this, the problem can easily be avoided by also checking if ```bar``` is ```null```:

```
console.log((bar !== null) && (typeof bar === "object"));  // logs false
```
To be entirely thorough in our answer, there are two other things worth noting:

First, the above solution will return ```false``` if ```bar``` is a function. In most cases, this is the desired behavior, but in situations where you want to also return ```true``` for functions, you could amend the above solution to be:

```
console.log((bar !== null) && ((typeof bar === "object") || (typeof bar === "function")));
```
Second, the above solution will return ```true``` if ```bar``` is an array (e.g., if ```var bar = [];```). In most cases, this is the desired behavior, since arrays are indeed objects, but in situations where you want to also ```false``` for arrays, you could amend the above solution to be:

```
console.log((bar !== null) && (typeof bar === "object") && (toString.call(bar) !== "[object Array]"));
```
However, there’s one other alternative that returns ```false``` for nulls, arrays, and functions, but ```true``` for objects:

```
console.log((bar !== null) && (bar.constructor === Object));
```
Or, if you’re using jQuery:

```
console.log((bar !== null) && (typeof bar === "object") && (! $.isArray(bar)));
```
ES5 makes the array case quite simple, including its own null check:

```
console.log(Array.isArray(bar));
```

#### *Question: What will the code below output to the console and why?*

```
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```

*Answer:* 

Since both ```a``` and ```b``` are defined within the enclosing scope of the function, and since the line they are on begins with the var keyword, most JavaScript developers would expect ```typeof a``` and ```typeof b``` to both be undefined in the above example.

However, that is not the case. The issue here is that most developers incorrectly understand the statement ```var a = b = 3;``` to be shorthand for:

```
var b = 3;
var a = b;
```

But in fact, ```var a = b = 3;``` is actually shorthand for:

```
b = 3;
var a = b;
```
As a result (if you are not using strict mode), the output of the code snippet would be:

```
a defined? false
b defined? true
```
But how can ```b``` be defined outside of the scope of the enclosing function? Well, since the statement ```var a = b = 3;``` is shorthand for the statements ```b = 3;``` and ```var a = b;```, ```b``` ends up being a global variable (since it is not preceded by the ```var``` keyword) and is therefore still in scope even outside of the enclosing function.

Note that, in strict mode (i.e., with ```use strict```), the statement ```var a = b = 3;``` will generate a runtime error of ```ReferenceError: b is not defined```, thereby avoiding any headfakes/bugs that might othewise result. (Yet another prime example of why you should use ```use strict``` as a matter of course in your code!)


#### *Question: What will the code below output to the console and why?*

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

*Answer:* 

The above code will output the following to the console:

```
outer func:  this.foo = bar
outer func:  self.foo = bar
inner func:  this.foo = undefined
inner func:  self.foo = bar
```

In the outer function, both ```this``` and ```self``` refer to ```myObject``` and therefore both can properly reference and access ```foo```.

In the inner function, though, ```this``` no longer refers to ```myObject```. As a result, ```this.foo``` is ```undefined``` in the inner function, whereas the reference to the local variable ```self``` remains in scope and is accessible there.

#### *Question: What is the significance of, and reason for, wrapping the entire content of a JavaScript source file in a function block?*

*Answer:* 

This is an increasingly common practice, employed by many popular JavaScript libraries (jQuery, Node.js, etc.). This technique creates a closure around the entire contents of the file which, perhaps most importantly, creates a private namespace and thereby helps avoid potential name clashes between different JavaScript modules and libraries.

Another feature of this technique is to allow for an easily referenceable (presumably shorter) alias for a global variable. This is often used, for example, in jQuery plugins. jQuery allows you to disable the ```$``` reference to the jQuery namespace, using ```jQuery.noConflict()```. If this has been done, your code can still use ```$``` employing this closure technique, as follows:

```(function($) { /* jQuery plugin code referencing $ */ } )(jQuery);```

#### *Question: What is the significance, and what are the benefits, of including 'use strict' at the beginning of a JavaScript source file?*

*Answer:* 

The short and most important answer here is that ```use strict``` is a way to voluntarily enforce stricter parsing and error handling on your JavaScript code at runtime. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions. In general, it is a good practice.

Some of the key benefits of strict mode include:

- Makes debugging easier. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions, alerting you sooner to problems in your code and directing you more quickly to their source.

- Prevents accidental globals. Without strict mode, assigning a value to an undeclared variable automatically creates a global variable with that name. This is one of the most common errors in JavaScript. In strict mode, attempting to do so throws an error.
- Eliminates this coercion. Without strict mode, a reference to a this value of null or undefined is automatically coerced to the global. This can cause many headfakes and pull-out-your-hair kind of bugs. In strict mode, referencing a a this value of null or undefined throws an error.

- Disallows duplicate parameter values. Strict mode throws an error when it detects a duplicate named argument for a function (e.g., function foo(val1, val2, val1){}), thereby catching what is almost certainly a bug in your code that you might otherwise have wasted lots of time tracking down.
Note: It used to be (in ECMAScript 5) that strict mode would disallow duplicate property names (e.g. var object = {foo: "bar", foo: "baz"};) but as of ECMAScript 2015 this is no longer the case.

- Makes eval() safer. There are some differences in the way eval() behaves in strict mode and in non-strict mode. Most significantly, in strict mode, variables and functions declared inside of an eval() statement are not created in the containing scope (they are created in the containing scope in non-strict mode, which can also be a common source of problems).

- Throws error on invalid usage of delete. The delete operator (used to remove properties from objects) cannot be used on non-configurable properties of the object. Non-strict code will fail silently when an attempt is made to delete a non-configurable property, whereas strict mode will throw an error in such a case.
