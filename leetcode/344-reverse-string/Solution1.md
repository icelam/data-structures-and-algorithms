# 344. Reverse String 
[&larr;&nbsp;Back to problem](./README.md)

## Approach 1: Recursion, In-Place, $${O}(n)$$ Space

**Does *in-place* mean constant space complexity?**

No. [By definition](https://en.wikipedia.org/wiki/In-place_algorithm), an in-place algorithm is an algorithm which transforms input using no auxiliary data structure.

The tricky part is that space is used by many actors, not only by data structures. The classical example is to use recursive function without any auxiliary data structures.

Is it in-place? Yes.

Is it constant space? No, because of recursion stack.

![Recursion Stack](./images/stack2.png)

### Algorithm

Here is an example. Let's implement recursive function `helper` which receives two pointers, left and right, as arguments.

* Base case: if `left >= right`, do nothing.
* Otherwise, swap `s[left]` and `s[right]` and call `helper(left + 1, right - 1)`.

To solve the problem, call helper function passing the head and tail indexes as arguments: `return helper(0, len(s) - 1)`.

### Implementation

Java: 
```Java
class Solution {
  public void helper(char[] s, int left, int right) {
    if (left >= right) return;
    char tmp = s[left];
    s[left++] = s[right];
    s[right--] = tmp;
    helper(s, left, right);
  }

  public void reverseString(char[] s) {
    helper(s, 0, s.length - 1);
  }
}
```

Python:
```Python
class Solution:
    def reverseString(self, s):
        def helper(left, right):
            if left < right:
                s[left], s[right] = s[right], s[left]
                helper(left + 1, right - 1)

        helper(0, len(s) - 1)
```

### Complexity Analysis

* Time complexity : $${O}(n)$$ to swap $$n/2$$ element.
* Space complexity : $${O}(n)$$ to keep the recursion stack.

