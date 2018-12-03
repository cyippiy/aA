# Miscellaneous

## HTML/CSS
* Name 5 benefits of HTML5
    * accessibility
        * html headings like    \<header>, \<footer>, \<nav>, \<section>
    * video/audio support
        * \<video> and \<audio> so you don't need to use \<embed> or flash player
    * doctype
    * cleaner code
        * previously you used div and class, now you can use \<section>, \<article>, etc
    * smarter storage
        * usage of local storage
    * better interactions
        * apis to build better UE and dynamic web app
            * canvas
            * drag and drop (DnD)
            * offline storage database
            * browser history management
            * document editing
            * timed media playback
    * game development
    * legacy/cross browser support
    * mobile
    * it's the "future"
* What is localStorage? How might you use it?
    * a mix of regular cookies and client-side database. can cache data, store info to load user's previous application state
* Why are media queries useful?
    * has a block of css when certain properties are true (browser window is under 600px, etc)
* What is mobile-first design
    * by designing the layout for mobile, we allow the page display load faster for smaller devices and we change the design when the width gets larger

## React

* In which order do the React Lifecycle methods (including the optional ones) run?
    * componentWillMount, componentDidMount, componentWillReceiveProps, shouldComponentUpdate, componentWillUpdate, componentDidUpdate, componentWillUnmount
* In which lyfecycle methods should you make asynchronous fetches for data?
    * componentsdidmount, componentsdidupdate 
* In which lyfecycle methods can you call setState?
    * componentDidMount, componentDidUpdate, componentWillReceiveProps
* Give one explanation for why we have to make AJAX requests in componentDidMount
    * guarentees that there's a component to update.
* What is a state tree in the context of Redux?
    * javascript object that keeps track of the current state of the application 
* Why don't we want to modify (i.e. mutate) our redux state?
    * you want to describe the actions for each change in state rather than modify the state. the state is redundant
* Describe in detail what a redux reducer is. 
    * takes current state, with the action being dispatched and returns a new state with respect to the dispatched action. pure function
* What makes it a pure function?
    * only returns values based on args, with no side effects. also does not modify args
* What is the role of the store in Redux?
    * holds the state status
* What does the subscribe method do in Redux?
    * listens for a particular state change and then dispatches an action accordingly
* What are presentational components?
    * components that is view oriented rather than actions.