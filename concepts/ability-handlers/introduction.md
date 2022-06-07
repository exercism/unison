# Introduction

In Unison, you can write your own abilities and handlers to supply different behaviors to your program. When a function calls one of the operations of an ability, Unison looks to the nearest enclosing handler to determine the next action to take. Handlers are special Unison functions where you can do things like pause and resume a computation, store state between calls to the ability, supply effectfully computed values to the rest of the program, or translate the ability into other Unison values. In short, they provide the implementation details for the ability.

Handlers follow some specific syntax conventions, but are conceptually a pattern match function. When writing a handler we are pattern matching on the request operations of the ability and dictating what should happen in each case when that operation is called.

```
structural ability KeyValue k v where
  get : k -> Optional v
  put : k -> v -> ()
```

A handler for the the `KeyValue` ability above will need to say what should happen when `KeyValue.put` and `KeyValue.get` are called in addition to showing what should occur when the a function is done calling the ability's operations, or never calls the operations in the first place.

