---
layout: post
title:      "Merge Sort"
date:       2019-10-08 14:03:58 +0000
permalink:  merge_sort
---


Merge sort is a divide and conquer algorithm that divides an unsorted array into subarrays that contain one element (which is considered sorted). We then repeatedly merge the subarrays until we have one sorted array.

Though there are many ways to implement merge sort, we start by writing out method that accepts a block, and we create a Proc in case no block is given:

```
class Array
def merge_sort(&prc)
prc ||= Proc.new { |x, y| x <=> y }
end
end
```

We then write our base case to return an array that contains a single element: 

```
class Array
def merge_sort(&prc)
prc ||= Proc.new { |x, y| x <=> y }
return self if self.count <= 1
end
end
```

Before we can finish the rest of our method, we need to create a helper method to take our subarrays and merges them in order into our final merged array.

```
class Array

  def merge_sort(&prc)
    prc ||= Proc.new { |x, y| x <=> y }

    return self if self.count <= 1

  end

  private
	
  def self.merge(left, right, &prc)
    merged = []

    until left.empty? || right.empty?
      case prc.call(left.first, right.first)
      when -1
        merged << left.shift
      when 0
        merged << left.shift
      when 1
        merged << right.shift
      end
    end

    merged.concat(left)
    merged.concat(right)

    merged
  end
end
```

With our merge helper method complete we can implement the rest of our `merge_sort` method. We next find the midpoint in the array and divide it into left and right subarrays. We then call `merge_sort` on each side which will recursively whittle the subarrays down to single elements:

```
class Array

  def merge_sort(&prc)
    prc ||= Proc.new { |x, y| x <=> y }

    return self if self.count <= 1
		
    midpoint = self.count / 2
    sorted_left = self.take(midpoint).merge_sort(&prc)
    sorted_right = self.drop(midpoint).merge_sort(&prc)
		
		

  end

  private
	
  def self.merge(left, right, &prc)
    merged = []

    until left.empty? || right.empty?
      case prc.call(left.first, right.first)
      when -1
        merged << left.shift
      when 0
        merged << left.shift
      when 1
        merged << right.shift
      end
    end

    merged.concat(left)
    merged.concat(right)

    merged
  end
end
```

Finally, we call out merge helper method like so:

```
class Array

  def merge_sort(&prc)
    prc ||= Proc.new { |x, y| x <=> y }

    return self if self.count <= 1
		
    midpoint = self.count / 2
    sorted_left = self.take(midpoint).merge_sort(&prc)
    sorted_right = self.drop(midpoint).merge_sort(&prc)
		
		Array.merge(sorted_left, sorted_right, &prc)

  end

  private
	
  def self.merge(left, right, &prc)
    merged = []

    until left.empty? || right.empty?
      case prc.call(left.first, right.first)
      when -1
        merged << left.shift
      when 0
        merged << left.shift
      when 1
        merged << right.shift
      end
    end

    merged.concat(left)
    merged.concat(right)

    merged
  end
end
```
Merge sort’s average/worst case run time is O(n log n), and best case is O(n).

