Just a bunch of practical functional mixins to make code more readable/maintainable

## Philosophy

A. all functions return a function which support only 1 input-argument
B. almost all functions return 1 output argument

> A+B = functional chain-orama!

## Functions

## _.trigger(fn)
 
trigger simply executes a function, but forwards original input as output.
this comes in handy when you don't want to break a flow/chain
 
> example:	_.flow( doSomethingWithInput, _.trigger( alert ), doSomethingElseWithInput )({foo:"bar"})
			
## _.either(a, b)
 
this will execute function b only when function a returns false/null/undefined 
 
> example: _.either(getUserByEmail,createUserEmail)("foo@gmail.com")
 
## _.when(f, g)
 
hipster if statement, only execute function g when function f does not return null/false/undefined 
 
> example: _.when( _.isString, console.log )("foo")
 
## _.flow( mixed_array_of_promises_and_functions )
 
improved version of _.flow, which also supports automatic resolving of promises
 
> example: _.flow( new Promise(.....), alert )("foo@gmail.com")
 
## _.lensOver(path, fn)
 
lens over allows i/o for a nested property 
 
> example: var updateBar = _.flow( -> 123, _.log )
>			_.lensOver( "foo.bar", updateBar )({foo:{bar:0}})  // sets 'foo.bar' to 123 (and prints in console)
 
## _.template_es6(es6_template)
 
simple es6 templates for in the browser
 
> example: _.template_es6('${foo}', {foo:"bar"})    // outputs 'bar'
 
## _.prefix(prefix, fn)
 
simple way to prefix a function which outputs a string 
 
> example: _.error = _.prefix("error: ", _.log)
 
## _.postfix(postfix, fn)
 
simple way to postfix a function which outputs a string 
 
> example: _.flow( _.get('.length'), _.prefix("items", _.log) )([1, 2, 3])
 
## _.log(str)
 
simple log function (which forwards input to output)
 
> example: _.flow( doFoo, _log, doBar )({input:"foo"})
 
## _.error(str)
 
simple error function (which forwards input to output)
 
> example: _.when( !hasFoo, _.prefix("something went wrong:", _error ) )({input:"foo"})
 
