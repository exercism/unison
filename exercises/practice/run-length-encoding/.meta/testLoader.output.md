# Testing transcript

```ucm
.> load ./src/runLength.u

  I found and typechecked these definitions in
  ./src/runLength.u. If you do an `add` or `update`, here's how
  your codebase would change:
  
    ⍟ These new definitions are ok to `add`:
    
      decode        : Text -> Text
      encode        : Text -> Text
      splitByEquals : [a] -> [[a]]

.> add

  ⍟ I've added these definitions:
  
    decode        : Text -> Text
    encode        : Text -> Text
    splitByEquals : [a] -> [[a]]

.> load ./test/runLength.test.u

  I found and typechecked these definitions in
  ./test/runLength.test.u. If you do an `add` or `update`,
  here's how your codebase would change:
  
    ⍟ These new definitions are ok to `add`:
    
      consistency                 : Text -> Text
      runLengthEncoding.test.ex1  : Test
      runLengthEncoding.test.ex10 : Test
      runLengthEncoding.test.ex11 : Test
      runLengthEncoding.test.ex12 : Test
      runLengthEncoding.test.ex13 : Test
      runLengthEncoding.test.ex2  : Test
      runLengthEncoding.test.ex3  : Test
      runLengthEncoding.test.ex4  : Test
      runLengthEncoding.test.ex5  : Test
      runLengthEncoding.test.ex6  : Test
      runLengthEncoding.test.ex7  : Test
      runLengthEncoding.test.ex8  : Test
      runLengthEncoding.test.ex9  : Test
      tests                       : [Result]
  
  Now evaluating any watch expressions (lines starting with
  `>`)... Ctrl+C cancels.

    43 | test> tests = runAll [
    
    ✅ Passed run-length encode a string, empty string : Passed 1 tests.
    ✅ Passed run-length encode a string, single characters only are encoded without count : Passed 1 tests.
    ✅ Passed run-length encode a string, string with no single characters : Passed 1 tests.
    ✅ Passed run-length encode a string, single characters mixed with repeated characters : Passed 1 tests.
    ✅ Passed run-length encode a string, multiple whitespace mixed in string : Passed 1 tests.
    ✅ Passed run-length encode a string, lowercase characters : Passed 1 tests.
    ✅ Passed run-length decode a string, empty string : Passed 1 tests.
    ✅ Passed run-length decode a string, single characters only : Passed 1 tests.
    ✅ Passed run-length decode a string, string with no single characters : Passed 1 tests.
    ✅ Passed run-length decode a string, single characters with repeated characters : Passed 1 tests.
    ✅ Passed run-length decode a string, multiple whitespace mixed in string : Passed 1 tests.
    ✅ Passed run-length decode a string, lowercase string : Passed 1 tests.
    ✅ Passed encode and then decode, encode followed by decode gives original string : Passed 1 tests.

.> add

  ⍟ I've added these definitions:
  
    consistency                 : Text -> Text
    runLengthEncoding.test.ex1  : Test
    runLengthEncoding.test.ex10 : Test
    runLengthEncoding.test.ex11 : Test
    runLengthEncoding.test.ex12 : Test
    runLengthEncoding.test.ex13 : Test
    runLengthEncoding.test.ex2  : Test
    runLengthEncoding.test.ex3  : Test
    runLengthEncoding.test.ex4  : Test
    runLengthEncoding.test.ex5  : Test
    runLengthEncoding.test.ex6  : Test
    runLengthEncoding.test.ex7  : Test
    runLengthEncoding.test.ex8  : Test
    runLengthEncoding.test.ex9  : Test
    tests                       : [Result]

```
