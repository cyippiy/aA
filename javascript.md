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