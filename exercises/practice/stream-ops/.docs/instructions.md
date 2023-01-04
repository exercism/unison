# Description

Implement basic `Stream` ability operations.

In functional languages, functions like `filter`, `map`, and
`reduce` are very common. Implement a series of basic functional combinators for a stream ability
without using existing functions. You'll need to write your own [ability handlers](https://www.unison-lang.org/learn/fundamentals/abilities/writing-abilities/) for this.

💡 We're going to call this ability `MyStream` to avoid conflicting with the existing `Stream` ability in the standard library.

The operations you'll need to implement are:

* `MyStream.fromList` (*given a list of elements, create a stream of elements* )
* `MyStream.toList` (*given a stream of elements, materialize it to a list*)
* `MyStream.toListWithResult` (*given a stream of elements, materialize it to a list alongside the result of the stream function*)
* `MyStream.ignore` (*given a stream of elements, ignore the emitted values, returning the results of the stream function*)
* `MyStream.filter` (*given a predicate and a `MyStream`, return the `MyStream` of all items for which `predicate(item)` is true*);
* `MyStream.map` (*given a function and a `MyStream`, return the `MyStream` of the results of applying `function(item)` on all items*);
* `MyStream.flatMap` (*given a function which produces a `MyStream` and a `MyStream`, return the `MyStream` of the results of applying `function(item)` on all items*)

