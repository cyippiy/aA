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