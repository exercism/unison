# Introduction

Computational effects happen when a function relies on or changes something about its environment. Maybe it reads a file, or throws an exception, or sends data to another place. Abilities represent one of the ways in which a Unison program can manage these computational effects. An ability pairs an interface which describes an effect's operations—what it does—with handlers that dictate how the effect should actually be performed—how it behaves. In programming literature they're known as "algebraic effects."

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
