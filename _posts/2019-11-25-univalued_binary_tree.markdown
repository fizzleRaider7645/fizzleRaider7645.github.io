---
layout: post
title:      "Univalued Binary Tree"
date:       2019-11-25 19:56:54 +0000
permalink:  univalued_binary_tree
---


In this week’s episode of easy LeetCode problems, I will walkthrough my solution to the Univalued Binary Tree. 

A binary tree is univalued if every node in the tree has the same value.
Return true if and only if the given tree is univalued.

Though iterating over a binary tree is the most efficient, recursion is used in this solution. First we need to define our base case.

```
def is_unival_tree(root, root_val = root.val)
    return true if root.nil?
    return false if root.val != root_val
```

If we reach an non-existent node, or nil, and have not yet found a node value that differs from the root node value, we know the tree is univalued. In order to keep track of the univalue I created a `root_val` parameter that takes in the root node to start. If we hit a node value that differs from the value stored in `root_val `we return false.

With the base case laid out we simply call `is_unival_tree` on the right and left branches of the tree:

```
def is_unival_tree(root, root_val = root.val)
return true if root.nil?
return false if root.val != root_val     
is_unival_tree(root.left, root_val) && is_unival_tree(root.right, root_val)     
 end
```

