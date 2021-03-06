# Reversed Arrays (Part 1)

Write a method that takes an Array as an argument, and reverses its elements in place; that is, mutate the Array passed into this method. The return value should be the same Array object.

You may not use `Array#reverse` or `Array#reverse!`.

Examples:

```ruby
list = [1,2,3,4]
result = reverse!(list)
result == [4, 3, 2, 1] # true
list == [4, 3, 2, 1] # true
list.object_id == result.object_id # true

list = %w(a b e d c)
reverse!(list) == ["c", "d", "e", "b", "a"] # true
list == ["c", "d", "e", "b", "a"] # true

list = ['abc']
reverse!(list) == ["abc"] # true
list == ["abc"] # true

list = []
reverse!(list) == [] # true
list == [] # true
```

Note: for the test case `list = ['abc']`, we want to reverse the elements in the array. The array only has one element, a String, but we're not reversing the String itself, so the `reverse!` method call should return `['abc']`.

**Solution**

```ruby
def reverse!(array)
  right_idx = -1
  half = array.size / 2
    
  (0..half - 1).each do |left_idx|
      array[left_idx], array[right_idx] = array[right_idx], array[left_idx]
      right_idx -= 1
  end
  
  array
end
```

**LS Solution**

```ruby
def reverse!(array)
  left_index = 0
  right_index = -1

  while left_index < array.size / 2
    array[left_index], array[right_index] = array[right_index], array[left_index]
    left_index += 1
    right_index -= 1
  end

  array
end
```

