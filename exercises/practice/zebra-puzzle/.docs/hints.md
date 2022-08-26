# Hints

## General

- There are a number of functions available for boolean expressions in the standard library. Check them out in the `Boolean` namespace on [Unison share](https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/types/Boolean).
- The Each ability allows you to operate on a list of elements as if it is one element, performing the desired function on "each" item. It can also be used to create combinations items, by calling Each on two different lists.
- Check out the [`guard` function on `Each`](https://share.unison-lang.org/@unison/code/latest/namespaces/public/base/latest/;/types/abilities/Each). It can be useful for when you want to conditionally return something from the `Each` ability.
- Given the number of unique combinations possible for this problem. You may run into space or time complexity issues. There are quite a few mechanisms for optimizing the search. Check out [backtracking](https://www.geeksforgeeks.org/backtracking-algorithms/) or [branch and bound](https://www.geeksforgeeks.org/branch-and-bound-algorithm/?ref=lbp) algorithms.
