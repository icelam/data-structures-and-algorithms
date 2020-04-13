# 136. Single Number
[&larr;&nbsp;Back to problem](./README.md)

## Approach 4: Bit Manipulation

### Concept

* If we take XOR of zero and some bit, it will return that bit
  * $$a \oplus 0 = a$$
* If we take XOR of two same bits, it will return 0
  * $$a \oplus a = 0$$
* $$a \oplus b \oplus a = (a \oplus a) \oplus b = 0 \oplus b = b$$

So we can XOR all bits together to find the unique number.

### Implementation

{% codegroup %}
```Java
class Solution {
  public int singleNumber(int[] nums) {
    int a = 0;
    for (int i : nums) {
      a ^= i;
    }
    return a;
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
        a = 0
        for i in nums:
            a ^= i
        return a
```
{% endcodegroup %}

## Complexity Analysis

* Time complexity : $$O(n)$$. We only iterate through `nums`, so the time complexity is the number of elements in `nums`.
* Space complexity : $$O(1)$$.
