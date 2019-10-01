---
layout: post
title:      "Binary Search"
date:       2019-10-01 17:48:37 +0000
permalink:  binary_search
---


Binary Search is a recursive algorithm we can use to find a target element in a sorted array. We implement binary search by finding the middle index like so:

```
def binary_search(array, target)
  mid = array.length / 2
end
```

Next we lay out our base case:

```
def binary_search(array, target)
  mid = array.length / 2
  return false if array[mid].nil?
  return true if array[mid] == target
end
```
In short, we return true if the element at the middle index is the target value we are looking for. However, if the target value is not in the array, array[mid] will eventually equal `nil`, meaning we need to return false.

With our base case established, we now check if the element at the middle index is larger or smaller than the target value. If the middle element is larger than the target, we call `binary_search` on all the elements before the middle element. We do the converse in the case that the middle element is smaller than the target.

```
def binary_search(array, target)
  mid = array.length / 2
  return false if array[mid].nil?
  return true if array[mid] == target
  if array[mid] > target
    left = array[0...mid]
    return binary_search(left, target)
    else
    right = array[mid + 1..-1]
    binary_search(right, target)
  end
end
```
The runtime of Binary Search is `O(n log n)` because we split the input size in half in each call.
