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
