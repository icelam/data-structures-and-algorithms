# 136. Single Number
[&larr;&nbsp;Back to problem](./README.md)

## Approach 1: List operation

### Algorithm

1. Iterate over all the elements in `nums`
2. If some number in `nums` is new to array, append it
3. If some number is already in the array, remove it

### Implementation

{% codegroup %}
```Java
class Solution {
  public int singleNumber(int[] nums) {
    List<Integer> no_duplicate_list = new ArrayList<>();

    for (int i : nums) {
      if (!no_duplicate_list.contains(i)) {
        no_duplicate_list.add(i);
      } else {
        no_duplicate_list.remove(new Integer(i));
      }
    }
    return no_duplicate_list.get(0);
  }
}
```
```Python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        no_duplicate_list = []
        for i in nums:
            if i not in no_duplicate_list:
                no_duplicate_list.append(i)
            else:
                no_duplicate_list.remove(i)
        return no_duplicate_list.pop()
```
{% endcodegroup %}

## Complexity Analysis

* Time complexity : $$O(n^2)$$. We iterate through `nums`, taking $$O(n)$$ time. We search the whole list to find whether there is duplicate number, taking $$O(n)$$ time. Because search is in the `for` loop, so we have to multiply both time complexities which is $$O(n^2)$$.
* Space complexity : $$O(n)$$. We need a list of size $$n$$ to contain elements in `nums`.
