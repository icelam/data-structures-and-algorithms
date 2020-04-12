# 202. Happy Number
[&larr;&nbsp;Back to problem](./README.md)

## Approach 3: Hardcoding the Only Cycle

> The first two methods are what you should think of during the interview. The third method is not what you will write in an interview, but for people who are curious about math because it is very interesting.

### Intuition
What's the biggest number that could have a next value bigger than itself? Well we know it has to be less than $$243$$, from the analysis we did previously. Therefore, we know that any cycles must contain numbers smaller than $$243$$, as anything bigger could not be cycled back to. With such small numbers, it's not difficult to write a brute force program that finds all the cycles.

If you do this, you'll find there's only one cycle: $$4 \rightarrow 16 \rightarrow 37 \rightarrow 58 \rightarrow 89 \rightarrow 145 \rightarrow 42 \rightarrow 20 \rightarrow$$. All other numbers are on chains that lead into this cycle, or on chains that lead into $$11$$.

Therefore, we can just hardcode a **HashSet** containing these numbers, and if we ever reach one of them, then we know we're in the cycle. There's no need to keep track of where we've been previously.

### Implementation

{% codegroup %}
```Java
class Solution {
    private static Set<Integer> cycleMembers =
        new HashSet<>(Arrays.asList(4, 16, 37, 58, 89, 145, 42, 20));

    public int getNext(int n) {
        int totalSum = 0;
        while (n > 0) {
            int d = n % 10;
            n = n / 10;
            totalSum += d * d;
        }
        return totalSum;
    }


    public boolean isHappy(int n) {
        while (n != 1 && !cycleMembers.contains(n)) {
            n = getNext(n);
        }
        return n == 1;
    }
}
```
```Python
def isHappy(self, n: int) -> bool:
    cycle_members = {4, 16, 37, 58, 89, 145, 42, 20}

    def get_next(number):
        total_sum = 0
        while number > 0:
            number, digit = divmod(number, 10)
            total_sum += digit ** 2
        return total_sum

    while n != 1 and n not in cycle_members:
        n = get_next(n)

    return n == 1
```
{% endcodegroup %}

### Complexity Analysis

* Time complexity : $$O(\log n)$$. Same as [Solution 1](./Solution1.md) and [Solution 2](./Solution2.md).
* Space complexity: $$O(1)$$. We are not maintaining any history of numbers we've seen. The hardcoded HashSet is of a constant size.
