---
language: Pony
contributors:
    - ["Rahul Sharma", "https://github.com/creativcoder"]
filename: learnpony/main.pony
---

Pony is an object-oriented, actor-model, statically typed, capabilities-secure programming language.It's actor-model because it has actors (similar to Erlang or Akka). These behave like objects, but they can also execute code asynchronously. Actors make Pony awesome.It a compiled language, rather than an interpreted one. In fact, it goes even further: Pony is an ahead-of-time (AOT) compiled language, rather than a just-in-time (JIT) compiled language. `ponyc` is the compiler.

By capabilites-secure, it means the language is:

* It's type safe. Really type safe. There's a mathematical proof and everything.

* It's memory safe. Ok, this comes with type safe, but it's still interesting. There are no dangling pointers, no buffer overruns, heck, the language doesn't even have the concept of null!

* It's exception safe. There are no runtime exceptions. All exceptions have defined semantics, and they are always handled.

* It's data-race free. Pony doesn't have locks or atomic operations or anything like that. Instead, the type system ensures at compile time that your concurrent program can never have data races. So you can write highly concurrent code and never get it wrong.

* It's deadlock free. This one is easy, because Pony has no locks at all! So they definitely don't deadlock, because they don't exist.

```pony
// This is a line comment.
/* This is a block comment. */
/* This block comment /* has another block comment */ inside of it. */

// Code Style Guide : Although indentations are meaningless in pony, 2 space indentations are preferred.

///////////////
// 1. Basics //
///////////////

/* A pony program needs to be in a directory (of any name) with a  .pony
file, and can be compiled with ponyc by passing in the directory name
*/

/* A simple program in Pony
Every pony program must start with a Main actor.
An Actor is similar to a class in other languages, but in addition it also
has asynchronous methods.
*/

// This is a actor type declaration, and they always start with a capital letter.
actor Main
// Actor can have methods
// Method names must start with a-z or _(a-z)
// A `new` method is a constructor for the actor Main, creates a new
// instance. In this case a new Main. 
  new create(env:Env) =>   
    env.out.print("Hello, Pony.")       // no ';' needed at the end


// A class type declaration in Pony
class Dragon
  // NOTE: every field in a class must be initialized in a constructor
  // otherwise the compiler throws an error

  // let declarations cannot be changed after assigned
  let name: String
  // var declarations can be changed.
  var _firepower:U64           // a '_' indicates a private field
  // A constructor ( the new keyword )
  new create(name':String) =>
    name = name'
    _firepower = 200
  // Pony can have multiple constructors
  new strong(name':String,firepower':U64) =>
    name = name'
    _firepower = firepower'
```


