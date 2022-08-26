# Introduction

Textual values or "strings" are represented by the `Text` type in Unison. `Text` values are Unicode characters which are created with the double quote syntax.

```
textValue : Text
textValue = "Hi there!"
```

The Unison standard library, `base` contains many useful functions for manipulating `Text` values under the namespace `base.Text`.

If you need to quote a special character (like double quotes or single quotes) or represent control characters like newline or tab, you can use the backslash `\` character as a character escape.

```
jsonValue = "{\"key\":42}"
```

A full list of valid escape characters can be found in [the official language docs][escape-chars].

You can also translate between a `Text` value and its representation as a `Char` (individual character) list with the `toCharList` and `fromCharList` functions. This means you can also make use of the functions on both the `List` and the `Char` type when you're working with `Text` values.

`Char` values are single character values represented with a question mark: `?a`

A list of `[?a,?b,?c]` can be translated into the `Text` value `"abc"` and vice-versa.
