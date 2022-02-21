# Javascript Book

### guide

```
console.log("Hello World")
let message="Hello World"; 
console.log(message)
// or
let {log} = console
log(message)
// or
let log2 = console.log.bind(console)
log2(message)
// log is a method on an object
let myconsole={
log:function(msg) {console.log(msg)}
}
myconsole.log(message)
```

console.log also prints undefined.
All javascript functions return something.
They will return undefined if nothing is specified to be returned;
It happens that the console also logs return values.
Which is why undefined also shows.

If you create a log which returns something, that will show instead.
```
myconsole.log2=function(msg) {console.log(msg); return 42}; 
myconsole.log2(message)
```
now 42 shows in the console.
This means you could log to the console without console.log, by returning a value;
```
myconsole.log3=function() {return message} 
myconsole.log3()
```

javascript functions have 3 methods on them
call,apply,bind
`console.dir(console.log)`
and look in the function prototype

you can call console.log like this
`console.log.call(null,message)`
the first argument is the execution context of the function
`console.log.call({},message)`
context is another word for object or state
```
myconsole.log4=function() {return this.message} 
myconsole.log4.call({message:"this test"}) 
let example1={message:"example object"} 
myconsole.log4.cal(exampleobject)
```

javascript will also soft bind the execution context if you choose not to pass it
the shorthand sytnax for calling a function does not allow you to pass an an execution context
`myconsole.log4()`
only arguments
but soft binding would look on the parent object for a message property
so you could do
`myconsole.message="from myconsole object" myconsole.log4()`
myconsole is implicitly passed in as the context.

Another way to override this soft binding behaviour is with bind.
bind is a method which returns a new function
`myconsole.log5=myconsole.log4.bind(example1) myconsole.log5()`
"example object" is logged. Because log5 is a new function with its "this" syntax replaced by "example5"
natively maybe it now looks like
`function() {return example1.message}`

sometimes in javascript, you will lose control over how an function gets executed. Javascript is just a scripting language working within a large environment. You will need to work with browser APIs, like addEventListener, which will call your function for you when they are triggered.
But understanding execution context and how you can set it ahead of time using bind you can avoid the wrong soft binding.

apply is similar to call. but changes the way you pass arguments to the function.

Javascript arrow functions do not have an execution context. if you use 'this' inside of an arrow function, it will be determined by the execution context of the next parent function in scope. ie.
`myconsole.log6=function() { let cb=() => console.log(this.message) cb() } myconsole.log6()`
will log the message property on myconsole, because that is the soft binding for log6, even though cb has no soft binding.
Arrow functions never set the 'this' keyword at all.
`let example2={message:"example2",log:() => console.log(this.message)}`
// logs undefined

### other
#### git
#### vscode
#### vim
#### json
### Strings

### Numbers
### Arrays

### Objects

### Functions
call,apply,bind
### DOM

#### APIs
#### document
.querySelector()
.querySelectorAll()
.createElement()
#### Element
.querySelector()
.querySelectorAll()
.appendChild()
.prependChild()
.replaceWith()
.replaceChildren()
.insertAdjacentElement()
.after()
.before()
.setAttribute()
.getAttribute()
.closest()
.animate()
.click()


innerHTML
insertAdjacentHTML
textContent
previousElementSibling
nextElementSibling

let nextel=document.createElement('div')
el.replaceWith(nextel)

childNodes returns a NodeLst which includes HTML elements as well as other nodes like text nodes (e.g. the spaces between the tags).

Element.children returns an HTMLCollection, not a NodeList 

Element.insertAdjacentHTML("afterbegin","<p>My new paragraph</p>")
"afterbegin":"afterend":"beforebegin":"beforeend";


#### Examples

### Icons
font-awesome
ionicons
heroicons

### SVG


### HTML
### CSS

### Node


### Testing
run functions you write first, before publishing them, to check they work
#### Jest

### Modules
unfortunately Javascript has different types of module syntax

common-js - require("")
es modules - import from
### Bundling
Bundlers resolve imports. They can convert one import syntax into another, making nodejs libraries run in the browser, for example. They also integrate with other tools, like transpilers
#### Webpack

### Transpiling
Transpilers read the syntax using an Abstract Syntax Tree and replace one piece of code with another. Used mostly for browser compatibility or converting JSX into React.createElement
#### Babel

### Linting
Its kind of like a spell checker for code. If finds syntax errors.
#### ESlint

### Typing
provides the computer with more information about your code. Catches errors.
Example is conditional returns (optional types)

### Documentation
There are auto generators for documentation

Docusaurus
JSDoc

### React

### HTTP
#### topics
1×× Informational
2×× Success
3×× Redirection
4×× Client Error
5×× Server Error

#### reference
100 Continue
101 Switching Protocols
102 Processing

200 OK
201 Created
202 Accepted
203 Non-authoritative Information
204 No Content
205 Reset Content
206 Partial Content
207 Multi-Status
208 Already Reported
226 IM Used

300 Multiple Choices
301 Moved Permanently
302 Found
303 See Other
304 Not Modified
305 Use Proxy
307 Temporary Redirect
308 Permanent Redirect

400 Bad Request
401 Unauthorized
402 Payment Required
403 Forbidden
404 Not Found
405 Method Not Allowed
406 Not Acceptable
407 Proxy Authentication Required
408 Request Timeout
409 Conflict
410 Gone
411 Length Required
412 Precondition Failed
413 Payload Too Large
414 Request-URI Too Long
415 Unsupported Media Type
416 Requested Range Not Satisfiable
417 Expectation Failed
418 I'm a teapot
421 Misdirected Request
422 Unprocessable Entity
423 Locked
424 Failed Dependency
426 Upgrade Required
428 Precondition Required
429 Too Many Requests
431 Request Header Fields Too Large
444 Connection Closed Without Response
451 Unavailable For Legal Reasons
499 Client Closed Request

500 Internal Server Error
501 Not Implemented
502 Bad Gateway
503 Service Unavailable
504 Gateway Timeout
505 HTTP Version Not Supported
506 Variant Also Negotiates
507 Insufficient Storage
508 Loop Detected
510 Not Extended
511 Network Authentication Required
599 Network Connect Timeout Error

### Errors
