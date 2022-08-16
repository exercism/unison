# Hints

## General

- Use the built-in [list type][list].

## 1. Define a function to return an empty language list

- You need to define a [Unison function function][named-function] with 0 arguments.

## 2. Define a function to add a language to the list

- You need to define a function with 2 arguments. The first argument is a [list][list] of language [text literals][string]. The second argument is a [text literal value][string].
- You can use list literal notation form.

## 3. Define a function to remove a language from the list

- You need to define a function with 1 argument. The first argument is a [list][list] of language [text literals][string].
- Check out Unison's syntax for [pattern matching on list elements][list-patterns]

## 4. Define a function to return the first item in the list

- You need to define a function with 1 argument. The first argument is a [list][list] of language [text literals][string].
- You can use the [`Optional` data type][optional] to represent if there is no value to return.

## 5. Define a function to return how many languages are in the list

- You need to define a function with 1 argument. The first argument is a [list][list] of language [text literals][string].
- Unison [provides a function][size] to count the length of a list.

## 6. Define a function to determine if the list includes a functional language

- You need to define a function with 1 argument. The first argument is a [list][list] of language [text literals][string].
- Your function should return a boolean value indicating whether `"Unison"` is a member of the list.

## 7. Define a function to create a string from the list

- You need to define a function with two arguments. The first argument is a [list][list] of language [text literals][string] and the second is a `Text` value to be used as a separator.

[list]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/types/data/List
[string]: https://www.unison-lang.org/learn/language-reference/literals/
[list-patterns]: https://www.unison-lang.org/learn/fundamentals/control-flow/pattern-matching2/#pattern-matching-on
[size]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/terms/data/List/size
[optional]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/types/Optional