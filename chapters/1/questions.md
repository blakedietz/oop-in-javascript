# Erik

Chapter 1 Primitives and Reference Types:

What is a function? A function is a way to manipulate an object.  What is the difference, then, between a function and a method?

On page 4, the author says that first-class functions are represented as objects - what does that mean, then, in defining first-class functions?

> "Even functions, which languages traditionally make you jump through hoops to get references to, are simply represented as objects in JavaScript, making them first-class functions."

Does this mean that first-class functions are things that act upon object values? Maybe I need to take a step back and chew on the concept of the object first!
Reference types: unlike primitive types which seem to be standard data types (numbers, strings, et al), reference types seem to be defined as objects, in memory, that the type reference ie it points to the space in memory where the object is located but not the object itself? How does the space an object takes up in memory add to the definition of an object? How important is this? I know that it is important for garbage collection but is it for anything else?
This paragraph is a bit confusing because it ties in (I believe) how a computer works in relation to the way a programming language works:

> "While other programming languages distinguish between primitive and reference types by storing primitives on the stack and references in the heap, JavaScript does away with this concept completely. Instead, there is the concept of a variable object that tracks variables for a particular scope. Primitive values are stored directly on the variable object while reference values place a pointer in the variable object. That pointer is a reference to a location in memory where the object is stored. There are, of course, other differences between the two types."

Interesting!!: when making assignments to variables (on pg 6 for reference), if you change the variable assignment on one object, it won't effect the other assignment. Why and how does this work?  Usually if you are making a = b and b = c, a = c with (and this is my understanding) if you change a, c would also change! IS MATH NOW DISPROVEN??
Equality signs: "=" mean assignment; "==" means equivalency; and "===" means that they are identical? is that the breakdown of the equal sign across the language?

Primitive Methods: makes sense that you can manipulate the data type with a method. But what is the difference between a method and a function?

Reference types: This paragraph is jam packed and I need some help unpacking its contents -> "Reference types represent objects in JavaScript and are the closest things to classes that you will find in the language. Reference values are instances of reference types and are synonymous with objects. An object is an unordered list of properties consisting of a name and a value. When the value of a property is a function, it is called a method." (pg 8)
In regards to reference types, I get that a type is an object; and that a value is particular instance of that type, but it breaks down when we talk about properties and methods.
In the conversation about constructors, I am unsure about why you would use a constructor and what it is there for.  I want to understand them because there are several references to best practices with constructors
Reference literals: first, very rad. Very convenient. In the example on page 10 and page 11 about literals, there are two ways to construct them.  Why choose one way over the other? They look identical except for some quotes.
Identification: there is a lot of talk about identifying objects, reference types, et al with 'typeof' and 'instanceof' - what is the importance of this? how useful is it?
Primitive Wrapper Types: what is a wrapper? I get that you would want to turn a primitive into an object but what use cases would illuminate the wrapper and how to use it? It seems its main purpose is to use methods on primitives?

# Blake

> What is a function? A function is a way to manipulate an object.

Not necessarily. A function can do many different things. I need to get you a more formal definition of what a function is. In mathematics, a function is a _conceptual object_ that takes elements from one set and transforms/maps it to another set. In programming a function is a logical division of your program, which is why they're often referred to as sub routines. [Subroutine definition on wiki](https://en.wikipedia.org/wiki/Subroutine). These functions can act like mathematical functions or be treated as small chunks of code that can be run.

> What is the difference, then, between a function and a method?

In my mind, functions can exist without objects. Methods exist on objects. I'm not sure if this is necessarily the formal definition. Let's see what some other resources say. [Stack overflow post on the topic](http://stackoverflow.com/questions/155609/difference-between-a-method-and-a-function). Looks like it's the case.

So in javascript a function looks like this:

```js
var add = function(x, y) {
  return x + y;
};

var result = add(1, 1);

console.log(result);
```

This is _one_ example of how a method could be attached to an object.

```js
var person = {
  age: 25,
  getAge: function() {
    return this.age;
  }
};

personAge = person.getAge();

console.log(personAge);
```

> On page 4, the author says that first-class functions are represented as objects - what does that mean, then, in defining first-class functions?
> ...

I think that I learned something new. Or that I relearned something that I wasn't familiar with. Either way, I'm learning with you!!! WOOOHOOOOO. Good questions. Here's a great [link](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function). The most interesting part specifically is this. I'm going to try and tie all of this together after your next question on it

```js
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those arguments
var adder = new Function('a', 'b', 'return a + b');

// Call the function
adder(2, 6);
// > 8
```

> Does this mean that first-class functions are things that act upon object values?

So we need to make a couple of distinctions here. We need to look at the concept of first-class functions vs the implementation.

The concept of first class functions:

Remember when thinking about all of this, that these concepts are not limited to Javascript. Instead they apply to many different programming languages. The concept of a first class function like the specification, the way that it works in the language is the implementation. First class functions need not always be objects, there are a plethora of ways to implement first class functions. Here's some great reading on this topic:

https://en.wikipedia.org/wiki/First-class_function

How first class functions are implemented in js:

So basically objects are able to be passed around and it turns out that javascript functions are objects. This is how the concept of first class functions are implemented in javascript.

> Reference types: unlike primitive types which seem to be standard data types (numbers, strings, et al), reference types seem to be defined as objects, in memory, that the type reference ie it points to the space in memory where the object is located but not the object itself? How does the space an object takes up in memory add to the definition of an object? How important is this? I know that it is important for garbage collection but is it for anything else?

All of these are good questions. Now you're getting into the underlying _implementation_ details of the concept of an object. While although some people would say that it's super important to understand, it's not something that you'll have to lean on initially. It is definitely something ot better understand as you mature though!

Regarding your question about garbage collection. It is important to know how paramaters can be modified when passing them into a function. The difference between pass by value and reference is important here. I'm going to simplify the explanation for pass by value vs reference in this discussion. Think of pass by value as taking a copy of a value when it gets passed into the function.

So for example

```js
function add1(param) {
  param = param + 1;
}

var foo = 7;
add1(7);
console.log(foo);
```

In this case 7 is a primitve of type Number. Numbers are passed by value and thus when foo is passed into the `add1` function, nothing happens to foo in the original context. It remains 7. Think of foo being copied to a completely different value when it is being accessed as `param` in `add1`.

On the other hand:

```js
function mutate(paramPassByRef) {
  paramPassByRef.foo = 'Hey there, what happened to my object';
}
var myObject = {
  bar: 'Something might happen when you pass me into a function'
};

mutate(myObject);
console.log(myObject.foo);
```

Here you see that when you run the code myObject somehow has a new property on it. In this case, the object is not a primitive and is thus pass by reference. That is the `mutate` function has a reference to the object in memory and can make direct changes to it. This is bad :(. It makes code hard to understand when changes happen without a clear interface.

> Interesting!!: when making assignments to variables (on pg 6 for reference), if you change the variable assignment on one object, it won't effect the other assignment. Why and how does this work?  Usually if you are making a = b and b = c, a = c with (and this is my understanding) if you change a, c would also change! IS MATH NOW DISPROVEN??
Equality signs: "=" mean assignment; "==" means equivalency; and "===" means that they are identical? is that the breakdown of the equal sign across the language?

Great questions again! A lot of people struggle on this one. Because you're not treating the `=` operator as you normally would. Unfortunately you need to throw away your notion of math in this scenario. The `=` operator is used for assignment. This is how you give values an alias. Think of these things as arrows to reference values.

So for example
a -> b
b -> c
Here we have that a is pointing to b and b is pointing to c. So when you reference a, you're technically referencing b and in turn c. So the final opearation
a -> c
is the same thing.

Again, it depends upon what type of value the property is. If it's a primitive changing a would not change c. However if it's an object changing a would indeed change c.

Regarding the `==` and `===` operators, yes, both are for equivalence, however, there's some nasty stuff around the operators that you'll eventually learn about. `===` is a more strict form of `==`. Type coercion takes place when you use the `==`.

First let's look at an example of normal comparison to how you're used to with `===` then we'll look at some funky javascript behavior with `==`.

When comparing two values with `===` it acts as you would hope it would behave.
```js
7 === 7 // true
'a' === 'b' // false
7 === '7' // false
```

However, something strange happens when you use `==`
```js
7 === 7 // true
'a' === 'b' // false
7 === '7' // true
```

Huh, what happened to that last one? I'm pretty sure that the textual version of 7 is not the same as the numeric version of 7. Well in javascript under the covers, type coercion is going on. Type coercion is an implicit conversion of a value of one type to another. This can be useful, but can also cause a lot of headaches. For example here's some more fun ones

```js
false == '' //true
'' === 0 // true lol wut?
0 == false
undefined == null // true wtf?
```

For each of those cases above the values are being implicitly converted from their original type into their boolean equivalent. You'll definitely want to read more about this. This is very important to understand as you start writing production ready code.

> Reference literals: first, very rad. Very convenient. In the example on page 10 and page 11 about literals, there are two ways to construct them.  Why choose one way over the other? They look identical except for some quotes.
Identification: there is a lot of talk about identifying objects, reference types, et al with 'typeof' and 'instanceof' - what is the importance of this? how useful is it?
Primitive Wrapper Types: what is a wrapper? I get that you would want to turn a primitive into an object but what use cases would illuminate the wrapper and how to use it? It seems its main purpose is to use methods on primitives?
