# Introduction

Unison represents true and false values with the `Boolean` type. There are only two values: `true` and `false`.

```unison
trueVariable = true
falseVariable = false
```

We can evaluate boolean expressions using the and, represented with `&&`; or, represented with`||`; and not, represented with `not`, operators.

```unison
trueVariable = true && true
falseVariable = true && false

trueVariable = false || true
falseVariable = false || false

trueVariable = not false
falseVariable = not true
```
