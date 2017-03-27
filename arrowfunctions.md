# ES6 Arrow Functions



## What are Arrow Functions?
An ``arrow function`` expression has a shorter syntax than a function expression and does not bind its own ``this, arguments, super, or new.target``. These function expressions are ``best suited for non-method functions,`` and they cannot be used as constructors.(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

Two factors influenced the introduction of arrow functions: shorter functions and non-binding of this.
(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)


ES6 fat arrow functions have a shorter syntax compared to function expressions and lexically bind the this value. Arrow functions are always anonymous and effectively turn function (arguments) { expression } into arguments => expression. If using an expression after an arrow, the return is implicit, so no return is required.(https://googlechrome.github.io/samples/arrows-es6/)


(Arrow Functions) ...have a concise syntax. Secondly, they have implicit returns, which allows us to write these nifty one-liners.

Thirdly, they don’t rebind the value of this when you use a arrow function inside of another function, which is really helpful for when you’re doing things like click handlers and whatnot.
(http://wesbos.com/arrow-functions/)

So – if the only purpose of your arrow function is to return something, there is no need for the return keyword. (http://wesbos.com/arrow-functions/)


## History Of Arrow Functions
Arrows have been part of JavaScript from the very beginning. The first JavaScript tutorials advised wrapping inline scripts in HTML comments. This would prevent browsers that didn’t support JS from erroneously displaying your JS code as text. You would write something like this:

``<script language="javascript">``
<!--
  document.bgColor = "brown";  // red
// -->
``</script>``
Old browsers would see two unsupported tags and a comment; only new browsers would see JS code.

To support this odd hack, the JavaScript engine in your browser treats the characters
as the start of a one-line comment. No joke. This has really been part of the language all along, and it works to this day, not just at the top of an inline ``<script>`` but everywhere in JS code. It even works in Node.

As it happens, this style of comment is standardized for the first time in ES6. But this isn’t the arrow we’re here to talk about.(https://hacks.mozilla.org/2015/06/es6-in-depth-arrow-functions/)

the arrow function binds the context lexically with the window object.


1. Lexical this binding – The value of this inside of the function is determined by where the arrow function is defined not where it is used.
2. Not newable – Arrow functions cannot be used a constructors and will throw an error when used with new.
3. Can’t change this – The value of this inside of the function can’t be changed, it remains the same value throughout the entire lifecycle of the function.(https://www.nczonline.net/blog/2013/09/10/understanding-ecmascript-6-arrow-functions/)

First and foremost, this binding is a common source of error in JavaScript.
It’s very easy to lose track of the this value inside of a function and can easily result in unintended consequences. Second, by limiting arrow functions to simply executing code with a single this value, JavaScript engines can more easily optimize these operations (as opposed to regular functions, which might be used as a constructor or otherwise modified).
(https://www.nczonline.net/blog/2013/09/10/understanding-ecmascript-6-arrow-functions/)

## Implementation in ES6



## Examples
An arrow function does not create its own this context, so this has its original meaning from the enclosing context. Thus, the following code works as expected:

function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| properly refers to the person object
  }, 1000);
}

var p = new Person();
Given that this is lexical, strict mode rules with regard to ``this`` are ignored. All other ``strict mode`` rules apply normally.




//filter ages older than 60 into const 'old'
(http://wesbos.com/arrow-function-examples/)
const ages = [23, 62, 45, 234, 2, 62, 234, 62, 34];
const old = ages.filter(age => age >= 60);
console.log(old)


## When Are Arrow Functions Best Used?

1. small, inline, single purpose
2. filtering through arrays or using other higher order functions
3. best suited for non-method functions
4. do not need explicit return. can return implicitly

arguments for arrow function
https://www.sitepoint.com/es6-arrow-functions-new-fat-concise-syntax-javascript/


## When Should You Not Use Arrow Functions?

1. Defining methods on an object(https://rainsoft.io/when-not-to-use-arrow-functions-in-javascript/)
2. Callback functions with dynamic context    ''
3. Invoking constructors (https://rainsoft.io/when-not-to-use-arrow-functions-in-javascript/)
4. Too short syntax (https://rainsoft.io/when-not-to-use-arrow-functions-in-javascript/)


## Key Points
0. Are more consise- small, inline, single purpose
1. do not need explicit return. can return implicitly (ex)
2. lexical this binding-  ``this``  does not bind to an arrow function but rather
    where (ie what function) it was called inside. (EX)
3. Not 'newable'- cannot be used as constructors
4. ``this`` inside an arrow function cannot be changed
5. Are anonymous - therefore do not give a stack trace.
6. best suited for non-method functions
7. are more suited to click handlers and filtering
8. Are good for minimizing higher order functions
9. cannot be named
