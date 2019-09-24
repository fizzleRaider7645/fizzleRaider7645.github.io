---
layout: post
title:      "Quicksort and Ruby"
date:       2019-09-24 12:36:54 +0000
permalink:  quicksort_and_ruby
---


Sorting an array is a task we often encounter when trying to solve various engineering problems. In Ruby, we have the `.sort` method that by default, sorts numbers in numerical order and letters in alphabetical order. For example:
```

arr = [18, -3, 2, 24, 29, 20, 15, 11, 4, -2, -5, 25, 16, 22, 7, 3, 5, 19, 23, 28, 6, 1, 17, 13, 30, 10, 27, 8, 21, 26, 12, -4, 9, -1, 0, 14]
arr.sort
=> [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30]
```

But how does this method work? It relies on the Quicksort algorithm, which is generally considered to be the fastest sorting algorithm we have. Quicksort is naturally recursive, so our first step in implementing it is to define a base case:

```
def quicksort(array)
  return array if array.length <= 1
end
```

The `return` statement above tells our code to return an array that has either one element in it, or is empty because both are already sorted.

Second, we select a “pivot element" like so:

```
def quicksort(array)
  return array if array.length <= 1
  pivot = array[0]
end
```

Above we are selecting the first element in the array as the pivot element, which means that we consider it as being already sorted. It is the element around which we will sort all the other elements in the array.

Third, we need to select all the numbers that are less than the pivot element, and all the elements greater than or equal to the pivot element:

```
def quicksort(array)
 return array if array.length <= 1
 pivot = array[0]
 left = array[1..-1].select { |el| el < pivot }
 rigth = array[1..-1].select { |el| el >= pivot }
end
```

Now that we have collections of all the elements smaller and larger/equal to the pivot element we call quicksort on both the left and right arrays and concatenate the recursive calls of each like so:

```
def quicksort(array)
 return array if array.length <= 1
 pivot = array[0]
 left = array[1..-1].select { |el| el < pivot }
 rigth = array[1..-1].select { |el| el >= pivot }
 quicksort(left) + [pivot] + quicksort(right)
end
```

We place the pivot element in an array because we can’t add a number and an array together. Now that we have it implemented, lets test it: 

`arr = [27, 3, 13, 12, 29, 11, -3, 8, 20, 9, -1, 24, -4, 17, 5, 30, 14, 0, 18, 26, 7, 2, 19, 16, 23, 10, 25, 4, 21, 1, -2, -5, 6, 28, 15, 22]`

```
quicksort(arr)
=> [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30]
```

It works! with the time complexity of O(n log n) in the best case, O(n log n) in the average case, and O(n^2) in the worst case.

