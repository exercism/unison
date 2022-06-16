# Tests

  ## Getting familiar with the Unison Codebase Manager

  The Unison Codebase Manager (UCM) is the tool that runs the Unison programming language and lets you navigate the Unison code you've written and saved.

  💡 Remember: Unison code is not saved as text-based file content. Because of this, we need a tool that lets us change and run Unison programs.

  Writing Unison code is as simple as opening your terminal of choice and running the `ucm` command in the directory where you'll be writing your Unison code. Then you can use your favorite text editor to create or open a file with a `.u` suffix, like `scratch.u` or `hello.u`. The bulk of your workflow will be navigating between the running `ucm` command line instance and your `.u` file. The UCM automatically listens to changes in your `.u` suffixed file upon saving the file.

  In lieu of a directory structure, Unison codebases are organized via "namespaces". You'll be exploring the standard library's namespace, called `base`, for useful functions and data types, and you'll be creating your own as you write Unison code. In the UCM, navigation in the codebase is done with the [`ls`](https://www.unison-lang.org/learn/ucm-commands/#ls), [`cd`](https://www.unison-lang.org/learn/ucm-commands/#cd), and [`view`](https://www.unison-lang.org/learn/ucm-commands/#view) commands—they're used for listing namespace content, moving throughout the namespace tree, and viewing source code, respectively.

  While you can navigate and view your codebase via the UCM CLI, you may also want to see a nice graphical representation of your work. You can do that by issuing the [`ui`](https://www.unison-lang.org/learn/ucm-commands/#ui) command in the UCM CLI. It will open a browser window with a view of the code in your codebase. The local codebase UI is also a great way to explore functions in our standard library, called `base`, which might be useful in accomplishing the exercises. [Read more about the local codebase UI here](https://www.unison-lang.org/learn/tooling/local-codebase-u-i/).

  You can practice Unison's programming workflow with the [Unison language tour](https://www.unison-lang.org/learn/tour/).

  ## Exercism testing setup

  ### Quick overview

  1. With the UCM watching the exercise directory, make your changes in the `<myFileName>.u` file
  2. Save the `<myFileName>.u` file
  3. If the file typechecks, run the `add` or `update` UCM commands
    * If the file does not typecheck, make changes to the code in your `<myFileName>.u` file until it compiles
  4. Run the `load <myFileName>.test.u` command in the UCM cli to bring the tests into scope and run them

  ### Detailed walk through

  If you're working on an Exercism problem on the command line, most likely you'll be implementing your solution in the directory named after the given exercise. For example, if the exercise is `hello-world`, you should open the `ucm` from the command line after having `cd`'ed into `~/exercism/unison/hello-world`. Make your implementation changes in the `hello.u` file, and when you're satisfied with your implementation, enter the `add` or `update` command in the Unison codebase manager CLI (UCM) to add your work from the file into the codebase.

  The file that contains the tests for each exercise is suffixed `.test.u`. You'll want to use the `load` command in the UCM to bring the tests into scope and run them. The `load` command takes a file path as its argument. Here's what that might look like for the hello world exercise:

  ```
  .> load hello.test.u
  ```

  You should see a message from the UCM about the terms that were brought into scope and, importantly, the result of running the test:

  ```

    ⍟ These new definitions are ok to `add`:

      hello.test : Test.Test
      tests      : [Result]

  Now evaluating any watch expressions (lines starting with
  `>`)... Ctrl+C cancels.


    6 | test> tests = runAll [hello.test]

    🚫 FAILED
  ```

  Let's say your tests didn't pass the first time. Switch back to editing your `myExercise.u` file, and upon saving you can `update`

  ```
  I found and typechecked these definitions in ~/Exercism/unison/hello-world/hello.u. If you do an
  `add` or `update`, here's how your codebase would change:

    ⍟ These names already exist. You can `update` them to your new definition:

      hello : Text

  .> update

  ⍟ I've updated these names to your new definition:

    hello : Text
  ```

  Next we can re-load our tests to see if anything changed!

  ```
  .> load hello.test.u
    Now evaluating any watch expressions (lines starting with `>`)... Ctrl+C cancels.


    6 | test> tests = runAll [hello.test]

    ✅ Passed : Passed 1 tests.
  ```

  ## Useful UCM Commands

  To see a list of available commands for interacting with your codebase, run `help` in the Unison Codebase Manager CLI. The list of UCM commands is also [described on our website](https://www.unison-lang.org/learn/ucm-commands/). Here are a few that might be helpful:

  * [`add`](https://www.unison-lang.org/learn/ucm-commands/#add): Adds the new definitions from the `.u` file to the codebase.
  * [`update`](https://www.unison-lang.org/learn/ucm-commands/#update): Works like `add`, except that if a definition in the file has the same name as an existing definition, the name gets updated to point to the new definition.
    * If the old definition has any dependents, update will automatically propagate the change if possible, or create a [`todo`](https://www.unison-lang.org/learn/usage-topics/workflow-how-tos/resolve-conflicts/) item for future refactoring.
  * [`load`](https://www.unison-lang.org/learn/ucm-commands/#load): Parses, typechecks and evaluates the given `.u` suffixed scratch file. Once typechecked and evaluated, you can add the terms to your codebase.
  * [`ls`](https://www.unison-lang.org/learn/ucm-commands/#ls): Lists the contents of a namespace
  * [`cd`](https://www.unison-lang.org/learn/ucm-commands/#cd): Navigates into the given namespace, creating the namespace if it does not exist
  * [`view`](https://www.unison-lang.org/learn/ucm-commands/#view): View the source code of a given Unison definition
  * [`ui`](https://www.unison-lang.org/learn/ucm-commands/#ui): Opens the local codebase UI
  * `exit`: Closes the UCM
