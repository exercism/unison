# Unison Basics

## Terms and functions

Terms and functions are the basic units of writing a Unison program.

A "term" is what we call a static value. It's defined with `name = expression`, optionally preceded by a type signature with the form `name : MyType`. Unison supports type inference, so you might see the type signature omitted for simple definitions.

```
myTerm = 42

helloThere : Text
helloThere = "Hello, World!"
```

Unison functions look like `myFunctionName argument1 argument2 = myImplementation`; they start with the name of the function followed by space-separated arguments.

```
getMax a b = Nat.max a b
```

Functions can optionally include a type signature. The last type on the right is always the final return type of the function, and each argument is separated by the function arrow `->`.

```
getMax : Nat -> Nat -> Nat
getMax a b = Nat.max a b
```

To call a function, use its name followed by its arguments separated only by spaces.

```
maximum = getMax 1 10
```

When calling a function, Unison will try to treat whatever comes to the immediate right as its argument, which might not always create the desired order of function evaluation.

Say we want to get the value `1` from the following expression

```
shouldBe1 = getMax 1 10 - 10
```

As written, `shouldBe1` evaluates to `0` because the implied function application order is `getMax 1 10`, which is `10` and then `10 - 10`, which is `0`.

You can use parentheses to regroup the expression into the desired order of operations.

```
shouldBe1 = getMax 1 (10 - 10)
```

## Multi line functions

Unison multi-line functions use indentation or `let` blocks to specify code boundaries, a.k.a "lexical scope."

```
swapOrder : Text -> Text -> Text -> Text
swapOrder beg middle end =
  newBeginning = end ++ middle
  newBeginning ++ beg
```

Everything at the same level of indentation shares the same scope, which is why we can reference the variable `newBeginning` in the last line.

## Namespaces and `use` statements

Namespaces are how we group and organize Unison functions. You can think of them as analogous to "directories." They provide structure and logical grouping.

You can bring the functions in a namespace into scope with a `use` statement.

Say you were writing a function which makes use of Unison `List` values. You know you'll need functions like `List.map` and `List.flatMap`, where `List` is the namespace and `map` and `flatMap` are functions. To avoid repeating yourself, you might choose to bring everything from the `List` namespace into lexical scope in your function like so:

```
listProcessing: [Nat] -> [Text]
listProcessing nats =
  use List
  map Nat.toText nats |>
  flatMap (fill 2)
```

The `use List` line disambiguates the references to `map` and `flatMap`. You can read more about [`use` statements here][use-statements].

## Unison's standard library

Unison's standard library is called `base`. If you followed the quickstart guide and have a codebase created locally, the standard library should have been automatically downloaded. You can browse the standard library documentation online at [Unison Share][unison-share-base].

## Comments and Documentation literals

Comments in Unison are a bit of an unusual feature. When writing Unison code, you can create text in your `.u` suffixed file that is not interpreted with the following syntax:

```
-- a single line comment
-- another single line comment

{-
  a multiline comment
  spanning multiple lines
-}
```

_However_, because Unison code is saved as a hash of its abstract syntax tree, not as text-based files on the file system, comments which are text-based "decorations" of a given Unison function or term in the file can't really be saved and re-rendered for sharing. If you would like to add a information to your Unison term in a way that will be stored for others to read and understand, you can use a documentation literal.

Documentation is a first-class value in the Unison programming language. That means a `Doc` element can be assigned to value, passed in as values to a function, or returned as a function's value. Documentation literal elements are opened and closed with double curly braces. Here's how we might use the `Doc` element as a comment.

```
myFunction: Nat -> Boolean
myFunction n =

  {{ when n is `4` we have a special important business logic exception}}

  if n === 4 then true
  else
    if isEven n then false
    else true
```

### Credits

This concept guide borrows liberally from [the official Unison documentation][unison-language-docs]

[use-statements]: https://www.unison-lang.org/learn/language-reference/use-clauses/
[unison-language-docs]: https://www.unison-lang.org/learn/
[unison-share-base]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest
