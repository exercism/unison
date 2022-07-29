# Hints

## General

- The [List documentation online][listDocs] mentions a few ways to access, query, and remove elements from a list.
- Some of the functions which operate on `Text` and or `List` return a value wrapped in the `Optional` type. `Optional` values can be either `Some value` or `None` and to operate on the internal value you can use `Optional.map`
- You can't return the `Optional` value given the type signature of these functions. Check out [Optional.fold][fold] or [Optional.getOrElse][getOrElse] for some ways to get rid of the `Optional` wrapper by supplying a default value if a `None` is returned.

## 2. Get log level from a log line

- While `Text` may not have a `toLower` function, maybe you can use `Char.toLower` and operate on the individual characters?


[fold]: https://share.unison-lang.org/latest/namespaces/unison/base/;/terms/Optional/fold/doc
[getOrElse]: https://share.unison-lang.org/latest/namespaces/unison/base/;/terms/Optional/getOrElse/doc
[listDocs]: https://share.unison-lang.org/latest/namespaces/unison/base/;/types/List
