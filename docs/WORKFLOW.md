# Workflow Tips

## Writing and evaluating Unison code

You write Unison code in files that have the `.u` file suffix. We call them "scratch" files because you use them to write Unison code, but the Unison Codebase Manager (UCM) is what ultimately stores and saves the content in those files. You'll still be submitting these files via the Exercism CLI, but the UCM can be considered a "source of truth" for Unison code.

While Unison does not have a REPL (Read Evaluate Print Loop), you can quickly evaluate Unison expressions in "watch expressions." In your `.u` suffixed file, start a line with `>` and enter an expression to the right.

```
> myFunction 42 "hi"
```

The UCM will show the results of evaluating the expression upon saving the file. This can be used when troubleshooting your exercise implementations.

For a more in-depth Exercism workflow, here's a [walk-through video][walk-through-vid] of implementing and testing an Exercism problem.

## Codebase organization

A Unison codebase is organized by "namespaces." Namespaces function a bit like directories in a file system, except instead of containing files, they contain your Unison types and functions. Namespace paths are separated by dots, `.`. For example, we can refer to the `Text` namespace in the `base` namespace with `base.Text`.

We recommend you create, or `cd`, into a namespace for each exercise that you're completing.

## Imports

Unison's syntax for managing and specifying imports is the `use` syntax. For example `use base.data.List` would bring all the functions under the `base.data.List` namespace into scope. This can be useful in situations where you are using a function like `map` on a `List` that needs to be to disambiguated from other `map` functions like `Optional.map`. You can also import specific functions by following the namespace with a space separated list of functions to bring into scope, as in: `use base.data.List tails head flatMap`.

You can use the `use` syntax both at the top-level of a file and within functions to specify imports. `use` clauses respect the rules of lexical scoping, so more nested imports take precedence over less nested imports.

## Standard library

The Unison standard library is called `base`. By default it is downloaded in new Unison codebases. You can browse the functions that are available to your implementations via the online repository for Unison code, [Unison share][unison-share], or via the [local codebase ui][local-codebase-ui], or by searching the Unison codebase manager (UCM). We'll describe that next.

## Navigating the Unison Codebase Manager (UCM)

A full list of UCM commands is available by entering `help` in the UCM, but here are a few tips and conventions.

You can search for terms by name or namespace prefix in the UCM with the `find` command, but `find` also supports _type based_ searching of a codebase. To search for a function by type signature, enter `find` followed by a space and colon, e.g. `find : [a] -> [[a]]`.

You can list the contents of a namespace with the `ls` command, for example `ls base.data.List` or `ls .exercism.helloWorld`. Many of the commands in the UCM will accept either relative namespace path arguments or fully qualified namespace arguments. Fully qualified paths start with a `.` representing the "root" of your codebase.

Move around the UCM with the `cd` command in the CLI. If a namespace doesn't exist, `cd` will _create_ one when you navigate to it. To go up a namespace you can use `cd ..`.

## Troubleshooting

__When I load the tests, the UCM cannot find my exercise implementation.__

Make sure you save your stub file in your text editor and `update` the terms in your codebase before loading the tests.

__I'm running into naming conflicts. I can't have two terms called `tests`.__

You can have two terms of the same name in different namespaces. If you're completing exercism exercises, it's recommended to create a separate namespace for each exercise so that the tests and stubs are separated from others.

__My tests pass locally but do not pass the test runner.__

Sorry about that! First check that your imports don't reference anything other than the standard library, `base`, and the functions that are defined in the `scratch` file under test. If that's the case, please let us know in the `#track-unison` Exercism slack or by filing an issue against [the Unison track repo][unison-track-repo].

__If you have any issues, please let us know! 🙂__

[walk-through-vid]: https://www.youtube.com/watch?v=4UMaaiJnWGY
[unison-share]: https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest
[local-codebase-ui]: https://www.unison-lang.org/learn/tooling/local-codebase-u-i/
[unison-track-repo]: https://github.com/exercism/unison
