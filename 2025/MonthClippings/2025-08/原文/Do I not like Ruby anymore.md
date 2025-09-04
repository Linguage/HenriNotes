---
title: "Do I not like Ruby anymore?"
source: "https://sgt.hootr.club/molten-matter/maybe-i-like-python-now/"
author:
  - "[[@steinuil]]"
published: 2024-05-28
created: 2025-08-26
description: "steenuil's blog"
tags:
  - "clippings"
---
I recently started working at a Python shop. The reasons behind this choice of employment are very much unrelated to the technology stack. Python is [not my favorite programming language](https://en.wikipedia.org/wiki/Euphemism). In fact, allow me to drop the euphemism and express my pure, unadulterated thoughts about it: I never liked Python, I see it as a huge red flag and I think the world would be a better place if we all decided to finally move on from it.

With that out of the way, let’s talk about how I’ve recently started to come around to Python and actually kind of like it in some aspects?

## I (used to) love Ruby

Ruby was my first love as a programmer. It is a playful, concise, elegant, expressive language that is built out of a handful of simple concepts with a good serving of syntax sugar on top.

- There’s no distinction between objects and primitives; everything is *actually* an object, [even `nil`](https://ruby-doc.org/3.3.1/NilClass.html)!
- You can [reimplement `if`](https://yehudakatz.com/2009/10/04/emulating-smalltalks-conditionals-in-ruby) using blocks and two additional methods on `NilClass` and `FalseClass` if you want!
- Method calls are just [syntax sugar for `send` ing messages to objects](https://ruby-doc.org/3.3.1/BasicObject.html#method-i-__send__)!
- You can define new methods on an object at call time [using `method_missing`](https://ruby-doc.org/3.3.1/BasicObject.html#method-i-method_missing)!

Ruby was clearly *designed* taking inspiration from such language designer’s languages as Smalltalk and Lisp, and as a budding Schemer with an interest in programming language design, that inspired me a lot.

Now, Python and Ruby were the two most popular “scripting” languages at the time. Ruby exploded thanks to Rails, and Python saw a lot of success as a language for data science and a better choice than Perl for command line tools and scripts.

The two languages were often compared and contrasted, and of course I, as a fan of Ruby, had a lot of opinions about Python.

## Python as a worse Ruby (and an even worse Scheme)

I kind of lied earlier when I said that Ruby was my first love as a programmer. The first time I started to really *grok* programming was when I learned a little bit of Scheme. I learned recursion before `for` loops, and I learned immutability before mutability.

As I said in the beginning of this post, I didn’t like Python. My dislike for it was best exemplified by its choice to make `if` a *statement* rather than an expression. If you want to assign a variable conditionally in Python you have to *declare* it first, and then *mutate* it from inside the `if` statement, and this just didn’t sit right with me.

(Yes, you can also use the `<then-expression> if <condition> else <else-expression>` inline conditional, but that looks weird to me even now.)

`lambda` s, my bread and butter as a Rubyist and Schemer, are replaced by horrible twisted versions of themselves that don’t allow statements. Even `print` was a statement before Python 3.0, so you couldn’t use it inside of a `lambda`. The horror!

In summary, Python to me just felt *unpleasant* to use. It’s a language that prides itself on having only one way to do things, and that way was usually not the one I wanted to use.

## Type systems for the untypable

At some point I found myself writing frontend code. JavaScript is not my favorite language, but TypeScript tried *very hard* to get me to love it.

I consider TypeScript to be the gold standard when it comes to type systems on top of dynamic languages. It is powerful enough to model almost all Real World JS, and while this approach introduces a lot of complexity, it also brought the language a lot of success.

TypeScript does a *bit* more work than your classic ML (as in [Meta Language](https://en.wikipedia.org/wiki/ML_\(programming_language\))) type system. TypeScript can:

- [Narrow](https://www.typescriptlang.org/docs/handbook/2/narrowing.html) a variable’s type based on the return type of a function you call on it!
- Manipulate types by [destructuring](https://www.typescriptlang.org/docs/handbook/2/keyof-types.html) and [constructing](https://www.typescriptlang.org/docs/handbook/2/mapped-types.html) them!
- [Make choices](https://www.typescriptlang.org/docs/handbook/2/conditional-types.html) while constructing a type based on subtyping rules!

The last two features in particular unlock some incredible type-level programming potential. TypeScript is one of the few type systems in which you can [play a text adventure](https://github.com/cassiozen/TDungeon) and [query a database](https://github.com/codemix/ts-sql)!

On top of being the most complex (and fun) type system of most languages out there, let alone those topping the TIOBE Index, TypeScript certainly makes JavaScript’s flaws a lot more bearable. It almost made me *enjoy* writing frontend code for a living.

## I changed

One thing I learned while writing TypeScript was that bad language features can be excused by some static analysis. *Maybe* not having `match` is ok when you have type narrowing based on control flow and unions. *Maybe* not having `if` expressions is ok when you can statically check that a variable was initialized after an `if` statement. *Maybe* [stringly typed](https://www.hanselman.com/blog/stringly-typed-vs-strongly-typed) variables are ok when you can statically enumerate the magic strings and ensure they are constructed correctly.

I also started writing quite a bit of Rust, which is a great language to show your functional programmer friends when you want to tell them that mutability is *actually fine*.

## Python changed

Python is not the same language it used to be. Now it supports type hints! And [`match` statements](https://docs.python.org/3/tutorial/controlflow.html#match-statements) with destructuring! Even `print` got turned into a normal function!

The type hints are easily my favorite feature. Not only do they provide type information to a good ecosystem of type checkers, but they can also be used by libraries to [validate schemas](https://docs.pydantic.dev/latest/) and [simplify defining web APIs](https://fastapi.tiangolo.com/).

I think they’re a great case study for integrating types in an existing ecosystem.

- They are built into the language, so unlike TypeScript where you need to insert a separate build step, there is no cost of adoption.
- They are orthogonal to type checking and inspectable from within the language, so libraries like Pydantic can leverage them to bring benefits even to users who don’t run a type checker. Everybody wins!
- The aforementioned libraries can serve as a gateway drug into the magical world of types ✨
- Keyword arguments. You can call any function using the argument names as keywords without any ceremony in the function definition. I wish every language had this feature!
- It has namespaces, which are pretty good.
- The lambdas are bad, but comprehensions and generator functions are neat. They remind me of F#’s sequence expressions.
- Having preferably only one way to do things is a good feature when you’re working with many people on a project.

## Ruby didn’t change

So where does that leave Ruby, my former favorite language? Well, Ruby didn’t change as much in the last 10 years. A bunch of performance work to benefit big applications like Rails, a couple of interesting features that didn’t seem to catch on, and a handful of new syntax additions that don’t amount to much. Nothing quite as game-changing as type hints. Matz doesn’t seem to care for them.

I still use Ruby for some scripts because I know it like the back of my hand, but… it just doesn’t feel the same. I get just a bit more irked by its quirks. I miss features from other languages. I long for keyword arguments, type hints, namespaces, I long for… Python!?

Maybe this is a sign that I’ve changed too much for Ruby. We had a lot of fun together, but it’s time to leave it behind. Goodbye Ruby, and thanks for all the chunky bacon.

And to Python I say: good job! You can have one of my midnight chicken nuggets. You deserve it.