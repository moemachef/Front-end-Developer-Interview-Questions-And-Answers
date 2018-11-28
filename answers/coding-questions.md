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
