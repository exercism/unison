# Hints

## General

* What might a simpler zipper over a (nonempty) list data structure do? Dropping one degree of movement in the zipper might help if you get stuck. A Zipper over a list would only need to care about moving left, moving right, and getting and setting an element at the focus.
* The `t` in `Zipper t a` represents the binary tree data structure for the purposes of this exercise. This allows the Zipper ability to "zip" around potentially more than one data structure!
