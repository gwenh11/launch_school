# 9. Multiply All Pairs

Write a method that takes two Array arguments in which each Array contains a list of numbers, and returns a new Array that contains the product of every pair of numbers that can be formed between the elements of the two Arrays. The results should be sorted by increasing value.

You may assume that neither argument is an empty Array.

Examples:

```ruby
multiply_all_pairs([2, 4], [4, 3, 1, 2]) == [2, 4, 4, 6, 8, 8, 12, 16]
```

**Solution**

```ruby
def find_pairs(arr1, arr2)
  combine = []
  arr1.each do |num1|
    arr2.each do |num2|
      combine << ([num1] + [num2])
    end
  end
  combine 
end

def multiply_all_pairs(arr1, arr2)
  find_pairs(arr1, arr2).map do |pair|
    pair.inject(1, :*)
  end.sort
end
```

**LS Solution**

```ruby
def multiply_all_pairs(array_1, array_2)
  products = []
  array_1.each do |item_1|
    array_2.each do |item_2|
      products << item_1 * item_2
    end
  end
  products.sort
end

def multiply_all_pairs(array_1, array_2)
  array_1.product(array_2).map { |num1, num2| num1 * num2 }.sort
end
```

#### Further Exploration

What do you think? Did you go about solving this exercise differently? What method did you end up using?

```ruby
# redo for interview assessment
=begin
input: two arrays of numbers
output: a new array 
    - contains product of every pair from the inputs
    - sorted in ascending order

rules:
- need every pair can be generated from combining two input arrays

data:
integers
arrays
  - nested arrays?

example: 
[2, 4], [4, 3, 1, 2]
2, 4
2, 3
2, 1
2, 2

4, 4
4, 3
4, 1
4, 2

algorithm:
- initialize 'sub_arrs'
- iterate through 'arr1' values:
  - iterating through 'arr2' values:
    - combine current value in arr1 and arr2 and put it in an array
    - append this array to 'sub_arrs'
- iterate through 'sub_arrs', transform each element to the product of the element in the subarray
- sort the return array
- return the result
=end

def multiply_all_pairs(arr1, arr2)
  sub_arrs = []
  arr1.each do |arr1_val|
    arr2.each do |arr2_val|
      sub_arrs << ([arr1_val] + [arr2_val])
    end
  end
  sub_arrs.map { |sub_arr| sub_arr.inject(:*) }.sort
end

p multiply_all_pairs([2, 4], [4, 3, 1, 2]) == [2, 4, 4, 6, 8, 8, 12, 16]
```

