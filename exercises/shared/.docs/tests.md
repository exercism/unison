# Tests

  ## Quick overview

  1. Make your changes in the `<myFileName>.u` file
  2. Save the `<myFileName>.u` file
  3. If the file typechecks, run the `add` or `update` UCM commands
    * If the file does not typecheck, make changes to the code in your `<myFileName>.u` file until it compiles
  4. Run the `load <myFileName>.test.u` command in the UCM cli to bring the tests into scope and run them

  ## Walk through

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
