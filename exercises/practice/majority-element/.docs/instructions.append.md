# Instructions append

- Bonus points: can you generalize your implementation to find the majority element of any type of List?
- Bonus points: is your implementation performant if there are many different elements to choose from when finding the majority?
- While you can implement the `majorityFinder` function in any way you choose, we've provided a few stubs which use the `MyStore` ability. (The `MyStore` ability is the same as `Store` from the standard library, but here we've given it a slightly different name for disambiguation.) You'll need to implement the `runWith` handler if you choose to use this ability. `runWith` returns both the result of running the function which uses the `MyStore` ability and the final state of the `MyStore`.
- You can read more about how ability handlers can track state in [the ability handler documentation][ability-handler-docs].

[ability-handler-docs]: https://www.unison-lang.org/learn/fundamentals/abilities/writing-abilities/
