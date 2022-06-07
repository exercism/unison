# About

In Unison, you can write your own abilities and handlers to supply different behaviors to your program. When a function calls one of the operations of an ability, Unison looks to the nearest enclosing handler to determine the next action to take. Handlers are special Unison functions where you can do things like pause and resume a computation, store state between calls to the ability, supply effectfully computed values to the rest of the program, or translate the ability into other Unison values. In short, they provide the implementation details for the ability.

Handlers follow some specific syntax conventions, but are conceptually a pattern match function. When writing a handler we are pattern matching on the request operations of the ability and dictating what should happen in each case when that operation is called.

```
structural ability KeyValue k v where
  get : k -> Optional v
  put : k -> v -> ()
```

A handler for the the `KeyValue` ability above will need to say what should happen when `KeyValue.put` and `KeyValue.get` are called in addition to showing what should occur when the a function is done calling the ability's operations, or never calls the operations in the first place.

## The parts of a handler

Let's look at a handler that enables interaction with a KeyValue store backed by an in-memory `Map`:

```
KeyValue.run : '{KeyValue k v} r -> r
KeyValue.run keyValueFunction =
  impl : Map k v -> Request (KeyValue k v) r -> r
  impl map = cases
    {KeyValue.get k -> resume} -> handle resume (Map.get k map) with impl map
    {KeyValue.put k v -> resume} -> handle resume () with impl (Map.put k v map)
    {pure} -> pure
  handle !keyValueFunction with impl Map.empty
```

Here's an overview of what this handler is doing:

1. This handler starts the `KeyValue` with an initial empty map value as the storage backing. This `Map` will be updated in subsequent calls to the request constructors of the ability.
2. The handler `get`'s values from the map when a program calls the `get` function and returns the expected value to the rest of the program
3. The handler `put`'s values into the map when a program calls the `put` function and updates the internal state of the handler by calling `impl` with an updated map
3. The handler passes through a `pure` value after all the interactions with the ability operations are done, or if the program doesn't end up using the ability at all.

### The type signatures of handlers

The type signature `KeyValue.run : '{KeyValue k v} r -> r` is read "KeyValue.run is a function which takes a computation that uses a `KeyValue` store in the process of returning some value, `r`, and eliminates the ability, allowing us to return that `r` value."

The single quote represents a thunk, or [delayed computation][delayed-computations].

Inside the `KeyValue.run` handler is a helper function with the signature `impl : Map k v -> Request (KeyValue k v) r -> r`. This is a common pattern for writing ability handlers. The helper function's first argument is the `Map` that we'll be updating to contain state internal to the handler. The second argument starting with `Request (KeyValue k v) r` is Unison's type which represents requests to perform the ability's operations (here those operations are `get` and `put`).

### Resuming computations

If you look at the cases in our pattern match, `{KeyValue.get k -> resume} -> ...`, you'll notice that we're doing more than just pattern matching on the operations of the ability like `get` or `put`, there's also a variable called `resume`; that's because a handler encapsulates a snapshot of the program state _as it is running._ Elsewhere in computer science literature the idea of "resuming computations" is called a [continuation][continuation-reference]. `resume` is a function whose argument is always the return type of the request operation in question, for example, `get : k -> Optional v` returns an `Optional v`, so that's the value provided to `resume` after looking up the key in the `Map`.

The fact that the continuation is reflected as a variable in the handler opens up possibilities for, say, rerunning the continuation, or even storing it!

### The handle ... with keywords

Many of the values in our handler have variable names that are up to us! For example, there's nothing magical about the word `pure` in the pattern match. You could call it `done` or `r` or `pineapple`. Likewise `resume` in the pattern match is just a convention. You could name it `theRestOfMyProgram` and call `handle theRestOfMyProgram` if you like. But there are two Unison specific keywords that have to be used in the handler: `handle ... with`. The `handle with` expression sandwiches two things: the first is the computation which performs the ability we're handling, and the second is the specific handler implementation which includes the `Request` type. Without it, there's nothing to communicate "hey we're operating on the request constructors of the ability" in the call to `!myKeyValueFunction` from the expression `handle !keyValueFunction with impl Map.empty`.

[continuation-reference]: https://en.wikipedia.org/wiki/Continuation
[delayed-computations]: https://www.unison-lang.org/learn/fundamentals/values-and-functions/delayed-computations/
