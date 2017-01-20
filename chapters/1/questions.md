Chapter 1 Primitives and Reference Types:

What is a function? A function is a way to manipulate an object.  What is the difference, then, between a function and a method?
On page 4, the author says that first-class functions are represented as objects - what does that mean, then, in defining first-class functions?
"Even functions, which languages traditionally make you jump through hoops to get references to, are simply represented as objects in JavaScript, making them first-class functions."
Does this mean that first-class functions are things that act upon object values? Maybe I need to take a step back and chew on the concept of the object first!
Reference types: unlike primitive types which seem to be standard data types (numbers, strings, et al), reference types seem to be defined as objects, in memory, that the type reference ie it points to the space in memory where the object is located but not the object itself? How does the space an object takes up in memory add to the definition of an object? How important is this? I know that it is important for garbage collection but is it for anything else?
This paragraph is a bit confusing because it ties in (I believe) how a computer works in relation to the way a programming language works:
"While other programming languages distinguish between primitive and reference types by storing primitives on the stack and references in the heap, JavaScript does away with this concept completely. Instead, there is the concept of a variable object that tracks variables for a particular scope. Primitive values are stored directly on the variable object while reference values place a pointer in the variable object. That pointer is a reference to a location in memory where the object is stored. There are, of course, other differences between the two types."

Interesting!!: when making assignments to variables (on pg 6 for reference), if you change the variable assignment on one object, it won't effect the other assignment. Why and how does this work?  Usually if you are making a = b and b = c, a = c with (and this is my understanding) if you change a, c would also change! IS MATH NOW DISPROVEN??
Equality signs: "=" mean assignment; "==" means equivalency; and "===" means that they are identical? is that the breakdown of the equal sign across the language?
Primitive Methods: makes sense that you can manipulate the data type with a method. But what is the difference between a method and a function?
Reference types: This paragraph is jam packed and I need some help unpacking its contents -> "Reference types represent objects in JavaScript and are the closest things to classes that you will find in the language. Reference values are instances of reference types and are synonymous with objects. An object is an unordered list of properties consisting of a name and a value. When the value of a property is a function, it is called a method." (pg 8)
In regards to reference types, I get that a type is an object; and that a value is particular instance of that type, but it breaks down when we talk about properties and methods.
In the conversation about constructors, I am unsure about why you would use a constructor and what it is there for.  I want to understand them because there are several references to best practices with constructors
Reference literals: first, very rad. Very convenient. In the example on page 10 and page 11 about literals, there are two ways to construct them.  Why choose one way over the other? They look identical except for some quotes.
Identification: there is a lot of talk about identifying objects, reference types, et al with 'typeof' and 'instanceof' - what is the importance of this? how useful is it?
Primitive Wrapper Types: what is a wrapper? I get that you would want to turn a primitive into an object but what use cases would illuminate the wrapper and how to use it? It seems its main purpose is to use methods on primitives?

Homework:
Is javascript an interpreted or compiled language? Interpreted which means it doesn't need to compile and gets read directly
What environments can javascript be executed from? I am assuming browsers here: Firefox mostly, then chrome and IE; I assume you can use a text editor as well!
Why can it be run in these environments? It can run on these environment because it doesn't need to be compiled down into machine language; in looking at stackexchange, it seems there are two parts to getting javascript to work - the engine and the runtime environment; the engine interprets the language and the runtime environment allows it to work with the outside world;``

> What is a function? A function is a way to manipulate an object.

Not necessarily. A function can do many different things. I need to get you a more formal definition of what a function is. In mathematics, a function is an object that takes an element from one set and transforms/maps it to another set. In programming a function is a logical division of your program, which is why they're often referred to as sub routines. (Subroutine definition on wiki)[https://en.wikipedia.org/wiki/Subroutine].

> What is the difference, then, between a function and a method?

In my mind, functions can exist without objects. Methods exist on objects. I'm not sure if this is necessarily the formal definition. Let's see what some other resources say. (Stack overflow post on the topic)[http://stackoverflow.com/questions/155609/difference-between-a-method-and-a-function].

> On page 4, the author says that first-class functions are represented as objects - what does that mean, then, in defining first-class functions?

I think that I learned something new. Or that I relearned something that I wasn't familiar with. Either way, I'm learning with you!!! WOOOHOOOOO. Good questions. Here's a great (link)[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function]. The most interesting part specifically is this.

```js
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those arguments
var adder = new Function('a', 'b', 'return a + b');

// Call the function
adder(2, 6);
// > 8
```

