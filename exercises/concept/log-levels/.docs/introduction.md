# Introduction

Textual values or "strings" are represented by the `Text` type in Unison. `Text` values are Unicode characters which are created with the double quote syntax.

```
textValue : Text
textValue = "Hi there!"
```

The Unison standard library, `base` contains many useful functions for manipulating `Text` values under the namespace `base.Text`.

You can also translate between a `Text` value and its representation as a `Char` (individual character) list with the `toCharList` and `fromCharList` functions. This means you can also make use of the functions on both the `List` and the `Char` type when you're working with `Text` values.

`Char` values are single character values represented with a question mark: `?a`

A list of `[?a,?b,?c]` can be translated into the `Text` value `"abc"` and vice-versa.
