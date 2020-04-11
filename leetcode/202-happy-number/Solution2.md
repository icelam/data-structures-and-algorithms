# 202. Happy Number
[&larr;&nbsp;Back to problem](./README.md)

## Approach 2: Dynamic Programming

### Intuition

As the problem has an **optimal substructure**, it is natural to cache intermediate results.  We ask the question $$\text{dp(i, j)}$$: does $$\text{text[i:]}$$ and $$\text{pattern[j:]}$$ match?  We can describe our answer in terms of answers to questions involving smaller strings.

### Algorithm

We proceed with the same recursion as in [Approach 1](./Solution1.md), except because calls will only ever be made to `match(text[i:], pattern[j:])`, we use $$\text{dp(i, j)}$$ to handle those calls instead, saving us expensive string-building operations and allowing us to cache the intermediate results.

*Top-Down Variation*

*Bottom-Up Variation*

###Complexity Analysis

* Time Complexity: Let $$T, P$$ be the lengths of the text and the pattern respectively.  The work for every call to `dp(i, j)` for $$i=0, ... ,T$$; $$j=0, ... ,P$$ is done once, and it is $$O(1)$$ work.  Hence, the time complexity is $$O(TP)$$.

* Space Complexity:  The only memory we use is the $$O(TP)$$ boolean entries in our cache.  Hence, the space complexity is $$O(TP)$$.
