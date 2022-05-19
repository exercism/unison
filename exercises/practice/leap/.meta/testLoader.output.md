# Testing transcript for hello exercise

```ucm
.> load /solution/src/leap.u

  I found and typechecked these definitions in
  /solution/src/leap.u. If you do an `add` or `update`, here's
  how your codebase would change:
  
    ⍟ These new definitions are ok to `add`:
    
      leap : Nat -> Boolean

.> add

  ⍟ I've added these definitions:
  
    leap : Nat -> Boolean

.> load /solution/test/leap.test.u

  I found and typechecked these definitions in
  /solution/test/leap.test.u. If you do an `add` or `update`,
  here's how your codebase would change:
  
    ⍟ These new definitions are ok to `add`:
    
      leap.test.t1 : Test
      leap.test.t2 : Test
      leap.test.t3 : Test
      leap.test.t4 : Test
      leap.test.t5 : Test
      leap.test.t6 : Test
      leap.test.t7 : Test
      leap.test.t8 : Test
      leap.test.t9 : Test
      tests        : [Result]
  
  Now evaluating any watch expressions (lines starting with
  `>`)... Ctrl+C cancels.

    30 |   runAll [
    
    ✅ Passed leap should be false when year is not divisible by 4 : Passed 1 tests.
    ✅ Passed leap should be false when year is divisible by 2 not divisible by 4 : Passed 1 tests.
    🚫 FAILED leap should be true when year is divisible by 4
    🚫 FAILED leap should be true when year divisible by 4, not divisible by 100
    🚫 FAILED leap should be true when year divisible by 4 and 5
    ✅ Passed leap should be false when year divisible by 100, not divisible by 400 : Passed 1 tests.
    🚫 FAILED leap should be true when year divisible by 400 and 100
    ✅ Passed leap should be false when year divisible by 4 and 100 : Passed 1 tests.
    ✅ Passed leap should be false when year divisible by 200, not divisble by 400 : Passed 1 tests.

.> add

  ⍟ I've added these definitions:
  
    leap.test.t1 : Test
    leap.test.t2 : Test
    leap.test.t3 : Test
    leap.test.t4 : Test
    leap.test.t5 : Test
    leap.test.t6 : Test
    leap.test.t7 : Test
    leap.test.t8 : Test
    leap.test.t9 : Test
    tests        : [Result]

```
