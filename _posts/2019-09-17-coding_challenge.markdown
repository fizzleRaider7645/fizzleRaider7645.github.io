---
layout: post
title:      "Coding Challenge"
date:       2019-09-17 11:39:25 +0000
permalink:  coding_challenge
---


I’ve been tackling various coding challenges in preparation for interviews, and I figured I’d share one. For this particular challenge, we start with an unsorted array of negative and positive integers. We are asked to segregate the array such that all the negative numbers are on the left side of the array, and all the positive on the left. My first attempt looked like this: 

```
def seg(array)
  neg = []
  pos = []
  array.each_with_index do |num, idx|
    if num < 0
      neg << num
      else
      pos << num
    end
  end
  neg.concat(pos)
end
```

Though this works, we can do better. Among other considerations, this solution requires we initialize two new arrays and then concatenate them at the end. How can we sort the array in place, and in one loop? After a few attempts I came across the following:

```
def seg(array)
  i = 0
  j = 0
  while i < array.length
    if array[i] < 0
      if j != i
        array[i], array[j] = array[j], array[i]
        j+=1
      end
    end
    i+=1
  end
  array
end
```

Unlike the first solution, the second solution sorts the array in constant space and O(n) time. Mission accomplished!
