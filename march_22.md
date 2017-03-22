- went over lab code from yesterday
- we're in the 3rd week
- there's usually a bit of burnout
- rate of retention drops, so we turn attention to gearing up for project week
- going over subjects of interest for the class
- looking at deployment today
- we will be using heroku

- process.env.PORT || 3000
- if there is nothing on the evironment variable PORT than use 3000....
- || is PORT
- if process.env.PORT is nothing, or undefined, then assign it to PORT 3000
- Turnery operators are important so look it up, it's a helpful shorthand that can be sometimes abused to make 
your code unreadable, so use it with your discression

LOGICAL PORT
-   ||
- we often use it in an IF statement
- if anything in IF is truthy, than the whole thing evaluates to true (?)
- There are only a few Falsy values
- FALSEY VALUES: 
    - false
    - null
    - undefined
    - 0
    - empty string ""
    - NAN

var name = 'string' || 0 || 'other'  (this will evaluate to string)
var name = '' || 0 || 'other' (this will evaluate to other)
var name = '' || 0 || '' (this will evaluate to empty string)
- no matter what, the logical operators assign the last thing (fyi yiy rarely see && anymore)....I don't understand this
- it evaluates to either the firt truthy value OR the last thing that it evaluates to
const PORT = process.env.PORT || 3000

EXAMPLES
 undefined ||0||false  (evaluates to false)
  undefined ||'0'||false (evaluates to '0')
  " || true || "  (evaluates to true)

  &&
  - returns the first falsy value or the last value it evaluates (oposite of OR)
   undefined && 0 && false  (evaluates to udefined)
  undefined && '0' && false (evaluates to undefined)
  " && true && "  (evaluates to empty string...first one)
   "" && " && " " (evaluates to empty string....first one)

   TURNERY operatorsis like an OR statement but an expression
   - you should only use them for now when assigning variables
   - it has two parts
   - expression ? true : false
   1. ? if this expression is true  it evaluates to this clause
   2. : 

var name = favAnumal = = = 'narwhal' (all of this is the expression)

var name = favAnumal = = = 'narwhal' ? 'Tom' (this is what it is if it's true)

var name = favAnumal = = = 'narwhal' ? 'Tom': 'Aaron' (this is what it will evaluate to if its anything other than tom)

var name = favAnumal = = = 'narwhal' ? 'Tom': 'Aaron'

EXAMPLE OF WHERE TO USE && outside of using it in a conditiona.:
function takesAfn(callback){
    console.log('in function);
    callback()
}

takesAfun(function(){})

- if we  run this  and don't pass anything in, it will give us takesAfn is not a function : so if you took out function(){})  from this: takesAfun(function(){})

- This is th same thing as above...this is an EXAMPLE of where you might use &&.  But && in general is not super common.  || operators are more common.  you shold know those patterns
function takesAfn(callback){
    console.log('in function);
    callback && callback();
}

takesAfun()


BACK TO: const PORT = process.env.PORT || 3000
- "process" is a keyword provided to us by node
- process is about what's going on around our program
 - one of the things on process is another object stored on a property called "ENV"
 - process.env (based on the source code, it shows us that it's an object)
 -  we can put stuff into the evironment that is sensative that we don't want to put into our code
 - we can't do this on the client side, we use this to do things like hide tokens
 -
 - GITHUB_TOKEN = "don't email me" node
 - we're storing information on process.env so that other things can get to it.
 - PORT = process.env.PORT || 3000
 - huroku is going to tell the server what port to run our site on 
 - when we run it locally, we run it on 3000
 - 

 heroku
 - check notebook for more information
 - Define CONFIG variables
 - there are two important methods
 1. herokuConfig --> shows you the content of your config variable
 2. herokuConfig:set ---> allows you to set an environmental variable
 - you can only push heroku from master (?)
 - whatever I set to heroku config set....it becomes avaialble to our server on process.env
 - by setting something to a config variable, we've added them to the environment
 - so our server can now get that code
 - this is wehre we can hide tokens
 - this is where we can pass off connection string that points to our cloud database if we're building a database
 - haveing a script file that we don't commit, is kind of cheating
 - TOP_SECRET_TOKEN="local secret" node index.js (this is how we introduce this hidden token to our local environment, after we've set it in our heroku environment
 )
 - because we have a server on our portfolio project, we have to use heroku to deploy it.
 
