# 202. Happy Number
[&larr;&nbsp;Back to problem](./README.md)

## Approach 1: Recursion

### Intuition

If there were no Kleene stars (the `*` wildcard character for regular expressions), the problem would be easier - we simply check from left to right if each character of the text matches the pattern.

When a star is present, we may need to check many different suffixes of the text and see if they match the rest of the pattern. A recursive solution is a straightforward way to represent this relationship.

### Algorithm

Without a Kleene star, our solution would look like this:

If a star is present in the pattern, it will be in the second position $$\text{pattern[1]}$$.  Then, we may ignore this part of the pattern, or delete a matching character in the text.  If we have a match on the remaining strings after any of these operations, then the initial inputs matched.

### Complexity Analysis

* Time Complexity: Let $$T, P$$ be the lengths of the text and the pattern respectively.  In the worst case, a call to `match(text[i:], pattern[2j:])` will be made $$\binom{i+j}{i}$$ times, and strings of the order $$O(T - i)$$ and $$O(P - 2*j)$$ will be made.  Thus, the complexity has the order $$sum_{i = 0}^T sum_{j = 0}^{P/2} \binom{i+j}{i} O(T+P-i-2j)$$. With some effort outside the scope of this article, we can show this is bounded by $$O\big((T+P)2^{T + \frac{P}{2}}\big)$$.
* Space Complexity:  For every call to `match`, we will create those strings as described above, possibly creating duplicates.  If memory is not freed, this will also take a total of $$O\big((T+P)2^{T + \frac{P}{2}}\big)$$ space, even though there are only order $$O(T^2 + P^2)$$ unique suffixes of $$P$$ and  $$T$$ that are actually required.
