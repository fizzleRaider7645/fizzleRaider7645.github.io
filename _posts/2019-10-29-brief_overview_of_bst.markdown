---
layout: post
title:      "Brief Overview of BST"
date:       2019-10-29 20:35:17 +0000
permalink:  brief_overview_of_bst
---


A Binary Search Tree is a data structure that has a few key characteristics. A node can have no more than two child nodes positioned left and right. The nodes to the left are strictly greater than the current node value, and the nodes to the right are strictly less-than, or equal to the value of the current node (node values that are equal to the current node value can technically go to either the right of left). With that in mind, if we are given a target value, how can we return the closest node?

Though the optimal solution for this problem is done iteratively, we will take a look at the recursive approach. First, we need to keep track of the closest node, which we will set to the value of the root node. For our recursive base case we will want to return the closest value if the current node is null. In other words, once we’ve hit a leaf.

With our base case out of the way we want to check the absolute difference between the target value and the current closest node, as well as the target value and the current node. If the absolute difference is less than the current closest, we will reassign closest with the current node value.

Next we check if the current node value is greater or less than the target value. If the current node value is greater than the target, we make a recursive call on the right branch, and vice versa in the case of less than.

The time complexity of this approach is, on average, O(nlog(n)), and O(n) in worst case.  

