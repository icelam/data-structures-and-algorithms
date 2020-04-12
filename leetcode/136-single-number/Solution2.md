# 136. Single Number
[&larr;&nbsp;Back to problem](./README.md)

## Approach 2: Hash Table

### Algorithm
We use hash table to avoid the $$O(n)$$ time required for searching the elements.

1. Iterate through all elements in `nums` and set up key/value pair.
2. Return the element which appeared only once.

### Implementation

{% codegroup %}
```Java
class Solution {
  public int singleNumber(int[] nums) {
    HashMap<Integer, Integer> hash_table = new HashMap<>();

    for (int i : nums) {
      hash_table.put(i, hash_table.getOrDefault(i, 0) + 1);
    }
    for (int i : nums) {
      if (hash_table.get(i) == 1) {
        return i;
      }
    }
    return 0;
  }
}
```
```Python
from collections import defaultdict
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        hash_table = defaultdict(int)
        for i in nums:
            hash_table[i] += 1
        
        for i in hash_table:
            if hash_table[i] == 1:
                return i
```
{% endcodegroup %}

## Complexity Analysis

* Time complexity : $$O(n \cdot 1) = O(n)$$. Time complexity of `for` loop is $$O(n)$$. Time complexity of hash table (dictionary in python) operation `pop` is $$O(1)$$.
* Space complexity : $$O(n)$$. The space required by `hash_table` is equal to the number of elements in `nums`.
