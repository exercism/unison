# Hints

## General

- Read about the [mental model for abilities][mental-model] in the intro to abilities documentation. It breaks down what your "internal computer" should be doing when executing code which uses abilities
- Take a look at [an example handler for the `Ask` ability][ask-handler]. It looks like it uses a helper function [Ask.provide.handler][ask-handler-implementation] that pattern matches on Ask's request constructor and a pure or pass-through case.

## 1. Implement a simple counter handler

- `Counter.run` is a handler which should contain some internal state: the current total count.
- Its customary for handlers to contain state as arguments to functions in the handler. Think about "updating the state" of the handler as "calling the handler again with an updated value"

## 2. Return the total count alongside the value produced by the function

- Experiment with the "pure" or "pass-through" case of the ability handler. What happens if you call "bug" instead of returning a value in the handler? Could you return _two_ instances of the value `{pure} -> (pure,pure)`, changing the type signature of the handlers accordingly?


[mental-model]: https://www.unison-lang.org/learn/fundamentals/abilities/
[ask-handler]: https://share.unison-lang.org/latest/namespaces/unison/base/;/terms/Ask/provide
[ask-handler-implementation]: https://share.unison-lang.org/latest/namespaces/unison/base/;/terms/Ask/provide/handler
