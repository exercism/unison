# Hints

## General

- Use the built-in [list type][list].
- In functional programming it's common to iterate through, inspect, or manipulate lists by [recursively pattern matching][functional-looping] on their elements until reaching the end of the list. In fact, many of the common functions defined for the list data type are based on these principles.

## 1. Define a function to return an empty language list

- You need to define a [Unison function function][named-function] with 0 arguments.

## 2. Define a function to add a language to the list

- You need to define a function with 2 arguments. The first argument is a [text literal value][string]. The second argument is a [list][list] of language [text literals][string].
- The list data type has a number of operators for manipulating lists, the "cons" (aka prepend) operator looks like `+:`.

## 3. Define a function to remove the left-most language from the list

- You need to define a function with 1 argument. The first argument is a [list][list] of language [text literals][string].
- Check out Unison's syntax for [pattern matching on list elements][list-patterns]. Pattern matching allows you to decompose the list into its constituent parts.

## 4. Define a function to return how many elements are in the list

- You need to define a function which takes in a [list][list] of language [text literals][string] and returns the size as a `Nat`.
- It's common to keep a running count of the number of elements seen using [recursion][functional-looping].

## 5. Define a function to determine if the list includes a given language

- You need to define a function with 2 arguments. The first is a [text][string] value and the second argument is a [list][list] of language [text literals][string].

## 6. Define a function to reverse a given list

- You need to define a function with 1 argument: the `List` of `Text` values.
- What happens if you call `List.foldLeft` on your list, passing in the `+:` operator as the first argument? What happens if you call `List.foldRight` with the `+:` argument?

[list]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/types/data/List
[string]: https://www.unison-lang.org/learn/language-reference/literals/
[list-patterns]: https://www.unison-lang.org/learn/fundamentals/control-flow/pattern-matching2/#pattern-matching-on
[size]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/terms/data/List/size
[optional]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/types/Optional
[functional-looping]: https://www.unison-lang.org/learn/fundamentals/control-flow/looping/#functional-looping