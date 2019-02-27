# Javascript

* Give a high level overview of what an object's prototype represents
    * prototype is an object that only has a constructor.
        * EG: Rabbit.prototype = { constructor: Rabbit }
* What are the differences between the __proto__ and prototype attributes?
    * \_\_proto\_\_ is a getter/setter for the prototype attributes
    * prototype attributes references 
* What happens when we do or don't explicity set an object's prototype?
    * javascript doesn't ensure the right constructor value. if we replace the default prototype, there might not be a constructor
* What is an object's default prototype?
    * constructor property
* What are the valid values for an object's prototype?
    * object or null
* What are the benefits of a Javascript closure?
    * allows for data encapsulation
* Formally define a Javascript closure
    * allows a function to access variables from an environment, even after leaving the scope
* Give an example of a closure
    * a say hi function, which takes in a name. then a function greeting is called with name. greeting cannot be accessed directly
* What is data encapsulation?
    * doesn't allow data to be directly interacted/exposed
* What is the difference between the memory heap and call stack in javascript?
    * memory allocation
    * call stack is where the callbacks/functions are stored until they are complete, then they get popped off
* What is one problem with programming languages that are fully single-threaded
    * blocking functions can hold up execution. need to wait for an action to be done before the next one
* Is Javascript a single-threaded language? Explain (Hint: This may not be a yes or no question)
    * Yes, it is but there's a JavaScript Runtime and an web API utilizing the browser
* When is using an IIFE necessary?
    * enables you to attach private data into a function
    * creates fresh environment
    * avoids polluting the global namespace
* What is the syntax for an IIFE?
    * (function(){do something})()
        * have a parenthesis around function declaration, then immediately invoke it after 
* What is the risk we face when using == vs ===?
    * checks for equality and coercion vs strict coercion
* When is the value of this evaluated?
    * runtime
* How does use strict affect the value of this?
    * won't be global object
* Without use strict, what is the value of this inside a named or anonymous function?
    * can be anything, based on what's evaluated during run-time
* What is the value of this in method style syntax?
    * object
* In which phase does hoisting occur?
    * compliation
* What is the difference between function hoisting and variable hoisting?
    * functions are always hoisted. variables like const and let are hoisted, but var is partially: var declaration is, but not reassignment
* What does the new keyword do in Javascript?
    * calls the constructor 
* What type of function is invoked with the new keyword? What does this function return?
    * newly created object is returned
* How can you stop event bubbling?
    * event.stopPropagation()
* What is the difference between event.target and event.currentTarget?
    * target grab the most deeply nested element
    * current is the one where the handler is currently running
* What does stopImmediatePropagation do?
    * stops bubbling and prevents all handlers on current element from running
* What is event delegation?
    * having a single handler on the common ancestor (parent) and having the event fire based on the trigger/action
* Discuss 4 differences between ES5 and ES6 that you find important
    * Block scope with let and const vs var
    * lexical "this"
        * will force `this` to always point to object where it's physically located within
    * "arguments"
        * can use `...args`. acts like an array but isn't actually an array
    * classes
        * syntax for declaring classes
    * stict mode
* What are the steps of a try..catch block in Javascript?
    * try block is executed
    * if no errors, catch(err) is ignored
    * if errors, catch is executed
* What type of errors to try..catch blocks work for?
    * runtime errors
* When creating a custom error, what attributes should it have?
    * message, name, and preferably stack
* What's the difference between the DOMContentLoaded and load event triggers?
    * browser loads HTML and DOM tree is built, but pictures/styles aren't loaded
    * resource and its dependent resources have finished loading
* Discuss the differences between let, const, and var. What are their respective scopings?
    * var is global scope
    * let and const are not hoisted, and block-scoped
* What happens when you enable strict mode in javascript?
    * can't use undeclared variables
    * makes bad syntax throw errors
        * attempt to reassign const variables, getter-setting variable, non-existent variable, non-existing object
* How does the rest/spread operator work in JS?
    * js doeesn't care how many arguments a function can be called with. excessive is okay
    * rest parameters can be called with ...args
        * thrown into an array
        * must be declared at the end
    * spread turns an array into a list of arguments
* What problem does bind solve in Javascript? How does it accomplish this?
    * preserving the correct context of an object's function
    * assigns this= by using bind.
        * ex: funcUser = func.bind(user)
* What is the syntax for passing arguments to the bind function?
    * func.bind(context, ...args)
* Does JS assign variables by value or by reference?
    * 
* What are the 7 different JS types?
  * 
* Explain the difference between + and -*/ in JS when it comes to coercion.
    * 
* How does prototypal inheritance work?
  * *