# About

Computational effects happen when a function relies on or changes something exterior to its immediate environment. Maybe the effect is reading from a file, or throwing an exception, or just changing a global variable. Abilities represent one of the ways in which a Unison program can manage these computational effects. An ability pairs an interface which describes an effect's operations—what it does—with handlers that dictate how the effect should actually be performed—how it behaves. In the programming literature they're known as "algebraic effects."

Unison's standard library contains a few commonly used abilities, which can be included in programs to represent error handling, global state, IO, and other useful effects.

```
divBy : Nat -> Nat ->{Abort} Nat
divBy a b =
  match b with
    0 -> Abort.abort
    n -> a / b
```

If a function performs an ability, you'll see it represent in curly braces, `{Abort}`, in the return type of the function.

## What are the benefits

Abilities are visible in the type signature of functions, so the effectful behavior of your program is still represented in the type system. A function can't secretly `throw` an exception or `emit` a value without an ability requirement appearing in the function signature, so you can reason about a program's behavior at the type level.

They support a separation of concerns between the purpose of an effect and how the effect is ultimately executed. This facilitates easy testing of effectful components and prevents the core of a program from being polluted with logic for managing the effect.

They allow for a coding style that is relatively free of boilerplate calls to `map` `flatMap` or other  "monadic plumbing 🪠"—particularly where multiple effects are being performed at once.

## Using Abilities in Unison code

Let's take a deeper look at a Unison function which uses an ability to represent a particular effect.

`divBy` below takes in two numbers and divides them. But what should happen if the denominator is zero? It's not a valid mathematical expression, so we need to represent that the program cannot return a value if given that argument.

The computational effect we're invoking is "we cannot compute a value" and the Ability we've chosen to represent that is called `Abort`.

```
divBy : Nat -> Nat ->{Abort} Nat
divBy a b =
  match b with
    0 -> Abort.abort
    n -> a / b
```

We know that this function is using the `Abort` ability because it appears in the function's return type in curly braces as `{Abort}`. Curly braces in Unison represent an _ability requirement_, and a function can have many ability requirements, in a comma separated list, like `{Abort, IO, Exception}`.

In the body of the function when `b` is `0` we're calling the operation of the ability, `Abort.abort`. This is our error case, where we communicate to the caller of `divBy` that something has gone wrong.

