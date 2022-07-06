# Instructions append

There are many ways to accomplish this exercise, but we've tailored this exercise for folks who'd like to practice writing their own [ability handlers][ability-handler-docs].

Write a `Zipper` ability that allows you to navigate through a binary tree data structure.

The `Zipper` ability itself is defined for you, but you'll need to implement the handler that allows it to navigate through our designated binary tree data structure.

Given the following binary tree, if we were to call `Zipper.right`, `Zipper.right`, `Zipper.up`, and then `Zipper.left` we should be standing at the node with a value of `5`.

```
     1
   /   \
  2     4
 /     /  \
3     5    7
```

For the purposes of this exercise, if you call `left` or `right` on a binary tree that doesn't contain a left or right branch, you can return the value at the present node.

## Things to ponder

In what way is an ability handler itself like a zipper? Could you consider the `continuation` of a function a pointer to the next "node" in your program? Could you store past calls to the continuation in your handler so you can navigate "back" to an earlier state?

What other data structures might you traverse in this way? Could you write a Zipper over JSON or one over the HTML DOM tree?
