A Ruby Begginers Guide to Big O Notation

Math kind of scares me, which sucks because as an aspiring programmer I know that I need to develope an at least passing familiarity with alorithms to reach my full potential.  After a lot of seaching online, I found an article by Robb Bell (rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/), which made the concept of "Big O Notation" a little less scary.  The code examples he provides were helpful to me in digesting in.  The purpose of this guide is to try and make it easier for DBC students (or anyone most familiar with Ruby) to digest these concepts.

O(1)
===========================
O(1) describes an alorithim that will always execute in the same time regardless of the input data set.

```Ruby

def is_first_element_nil(array)
  if array[0] == nil
    return true
  else
    return false
  end
end
```

O(N)
============================
O(N) describes an algorithim whose time to execute will grow linearly in proportion to the input data set.  A linear search is a good example of O(N).

```Ruby

def contains_number(number, array)
  i = 0
  for i in (0..array.length - 1)
    return i if number == array[i]
  end
    return nil
end
```

O(N^2)
==============================
O(N^2) describes an algorithim time to execute is directly proportional to the square of the input data set.  This is seen in alorithims the contain nested iterations.  A good example of this is the infamous bubble sort.

```Ruby

def bubble_sort(list)
  return list if list.size <= 1 # already sorted
  swapped = true
  while swapped
    swapped = false # maybe this time, we won't find a swap
    0.upto(list.size-2) do |i|
      if list[i] > list[i+1]
        list[i], list[i+1] = list[i+1], list[i] # swap values
        swapped = true # found a swap... keep going
      end
    end
  end
  list
end

O(log N)
==============================
A binary search is an example of O(log N).

```Ruby

def binary_search(number, array, min = 0, max = array.length - 1)
  array.sort!
  return -1 if max < min
  mid = (min+ max) / 2
  case
  when array[mid] > number then binary_search(number, array, min, mid-1)
  when array[mid] < number then binary_search(number, array, mid+1, max)
  else mid
  end
end

```





























