- today's lab is goign to be trace the lab and note it
- transitions in state can be run through transformations and filters...taking the functional program method even further.
- soemthing changing, some sort of input passing through a number of filters until it reaches its final state is prevelant right now
- so we're going to be working through middleware
- general 301 review

FUNCTIONAL PROGRAMMING
- we're at the akeard stage of actually understanding something and just being able to use it
- 3 major concepts in higher order functions.
1. concept of expressions and evaluations
2. the diff between calling functions and passing functions
3. writing a function that takes another function as a an argument

- the behaviors of our program exists in different files now, based on their functionality (view, controller, model)
- we have to have behaviors that can be passed off to other sets of behaviors...they have to be passed off to different files.
- we looked at REPOVIEW file in lab from Tuesday 3.21 lab
- giving certain parts of our code, jobs...the repoView is responsible for taking data, knowing it where it is and displaying it properly
- clearing out a UL and hiding the other panels in html (looking at the iu function)
- repos.with('nae).map(render).....line 23
- we can assume that since we're calling map, we're ending up with an array
- we have to find this repos thing....which will be in model...do a search in vs code
- I know that it was probably assigned to module. somewhere, because it's available
- I find that in the model section....and I see that repos is returning an array of objects.
- now I have to figure out what "with" method is
- we're looking at repos.woth('name') to see what it is that we're calling map on (line 23 in repoView)
- we're comparing it to repos.woth = attr => repos.all.filter (line 23 on repos file)
- repos.all is an array of objects from the ajax call....on that we're calling filter.  Filter takes a function with evaluates to something....repo=>repo[att] becomes what is returned from repos.with
- you're not supposed to use arrow functions as properties of objects.
repo => repo[attr];....repo is the argument name.  repo is what is getting passed into the function
- what is getting returned from this function
- if it returns a string, it thinks it's true
- if it's undefined, it thinks its false
- if it's true, it gets into the array.
- repos.with('name) evaluates to an array 
- now we pass the function into map...we pass render
- we need to understand the parts of it...you can't consider the whole line as one thing...you must understand that the line, the statement is made up of individual expressions.  you must break down those expressions
- you must evaluate the expressions
- repo is an objext that has all of our resources on it.  with is a method that calls filter and returns a set of object that have a value stored at this attribut.
- render function gives a string of HTML
- then we're  appending that string of HTML strings
- repos. with is a subset of repos.all
- all of that stuff that within the append method....it takes all of that, the html string and appends it to the UL
- 

MIDDLWARE:
- center an entire page, by wrapping it in an element like main and then setting main to margin 0 auto
- we use routes to manage transitions in our application
- a click changes what everyone sees...we have to tell soemthing on the other end about what was happening
- what the count is = our application state
- we have to tell some other part of the application where we just were
- throwing stuff in the global scope doesn't quite cut it
- we can't store all of our application states in routes
- the problem is that we need to ma
- all the functions that get passed into PAGE (in routes) are getting passed an argument
- the argument is called the context
- the context is an object that gets passed to all of these functions (it's something attached to PAGE functions)
- for every function that we're passing in as handler for our routes, there is a function attached to it called context.
- this is getting passed each time, if we want to interact with it, we have to give it a name.
page('\one)
- PARAMS (the colon thing)...anything beyond the : in the URL
- we can use this to
- middleware and client side routing deals with, all these different parts of the application that don't know about eachother....something on the other end must know abot what's going on with all aspects of our application
- the way we we take care of this is a combination of our URL PARAMS
- we're going to use parts of the URL to vary what we get on the other end
- we have this context object and CONTEXT has a property called PARAMS that is also an object
- CONTEXT is an object that represents info about the state that we're transitioning FROM
- the main part of it for our purposes, for using the URL is the PARAMS...which is an object
- the way that you add PARAMS to your route is with a colon :
- page ('/one/:someNumber', (context))
- and now in HTML you ad something
- on PARAMS gets stored a value that gets added to the URL
- PARAMS is an object that has stored on it information that's in the URL
- the trick is that we have to get something worthwhile into the URL
- so we add a new function to our module
- I'm going to add an event listener to 

oneView.handlelink

- page has a function if you pass it a string, it will navigate there
- if you pass it ('/one/${count}); it will navigate there

2.
- inbetween these transitions in state
- you can add things into what's happening durring the transition
- PAGE as a function takes a function and a number of things...each one of those fucntions gets passed a number of things that includes context object function as well as
- (ctx, next)
- ctx = context...it's what we call it
- we add a property to the function and when we're done with it, we call next.

finction freiendlyGreeting(ctx,next){
    ctx.greeting = 'Hi!'
    next();
}

page('/first', friendlyGreeting, ctx =>{
    console.log(ctx.greeting+ 'first;
});

- without the next call, it doesn't know to pass on to the next
- this comes in handy beca this allows you to process data as you go along...you can add parts to it.
- if you put next function into FECTH ALL you can tell it to wait until it gets data that it can use to run.
- you can use NEXT in asynch to tell it to wait for more information


LAB:
- in today's lab we have a bunch of functions that we have to trace.
- 