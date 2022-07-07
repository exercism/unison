# Unison Lists

Lists are used in the Unison programming language to represent a finite, ordered collection of elements. They're written with comma-separated elements in square braces:

```
emptyList = []

listNats : [Nat]
listNats = [1,2,3,4]

listText : [Text]
listText = ["hello", "world"]
```

Unison implements lists as a finger tree, allowing for fast access of the first and last element. You can read more about the underlying implementation in the [standard library List documentation][list-docs]. Appending single elements to either side of the list can be done with the `+:` and `:+`:

```
myList = [1,2,3,4]

> 0 +: myList :+ 5
  ⧩
  [0, 1, 2, 3, 4, 5]
```

Concatenating lists is supported with the `++` operator:

```
> [1,2] ++ [3,4,5]
  ⧩
  [1, 2, 3, 4, 5]
```

The standard library, `base` contains a variety of functions available for `List` transformations. Check them out by using the `find` command in the UCM or by exploring the `List` namespace in [Unison share][list-docs].

[list-docs]: https://share.unison-lang.org/latest/namespaces/unison/base/;/types/List
