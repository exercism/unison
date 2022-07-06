# Instructions append

## About the Stream ability

A `Stream` is a Unison ability that is used to emit values.

You might use the `Stream` ability if you have a function which should produce values as a secondary effect while it is being called. For example, this function returns the last value of the list, but emits a running total as each element is seen:

```
emitRunningTotal : '{Stream Nat} Nat
emitRunningTotal = 'let
  use Nat +
  List.foldLeft (
    acc a -> let
      runningTotal = acc + a
      Stream.emit runningTotal
      a
    ) 0 [1,2,3,4,5]
```

We can materialize the Stream as a List alongside the return value of the function which produces it with an ability handler:

```
> Stream.toListWithResult! emitRunningTotal
  ⧩
  ([1, 3, 5, 7, 9], 5)
```
