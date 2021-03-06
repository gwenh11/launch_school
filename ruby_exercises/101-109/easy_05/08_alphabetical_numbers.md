# 8. Alphabetical Numbers

Write a method that takes an Array of Integers between 0 and 19, and returns an Array of those Integers sorted based on the English words for each number:

zero, one, two, three, four, five, six, seven, eight, nine, ten, eleven, twelve, thirteen, fourteen, fifteen, sixteen, seventeen, eighteen, nineteen

Examples:
```ruby
alphabetic_number_sort((0..19).to_a) == [
  8, 18, 11, 15, 5, 4, 14, 9, 19, 1, 7, 17,
  6, 16, 10, 13, 3, 12, 2, 0
]
```

**LS Solution**

```ruby
NUMBER_WORDS = %w(zero one two three four
                  five six seven eight nine
                  ten eleven twelve thirteen fourteen
                  fifteen sixteen seventeen eighteen nineteen)

def alphabetic_number_sort(numbers)
  numbers.sort_by { |number| NUMBER_WORDS[number] }
end
```

**Further Exploration**

Why do you think we didn't use `Array#sort_by!` instead of `Enumerable#sort_by?`

For an extra challenge, rewrite your method to use `Enumerable#sort` (unless you already did so).

The calling object is an Array. Array has its own `sort_by!`, so it will use this method. If it didn't have its own version of `sort_by!`, it would have used `Enumerable#sort_by`

```ruby
NUMBER_WORDS = %w(zero one two three four
                  five six seven eight nine
                  ten eleven twelve thirteen fourteen
                  fifteen sixteen seventeen eighteen nineteen)

def alphabetic_number_sort(numbers)
  numbers.sort { |num1, num2| NUMBER_WORDS[num1] <=> NUMBER_WORDS[num2] }
end
```
