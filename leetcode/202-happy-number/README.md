# 202. Happy Number
> Level: Easy  
> Related topics: Recursion  
> Link: [https://leetcode.com/problems/happy-number/](https://leetcode.com/problems/happy-number/)

## Problem

Write an algorithm to determine if a number `n` is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it **loops endlessly in a cycle** which does not include 1. Those numbers for which this process **ends in 1** are happy numbers.

Return True if `n` is a happy number, and False if not.

#### Example
```
Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

## Solution
* [Approach 1: Recursion](./Solution1.md)
* [Approach 2: Dynamic Programming](./Solution2.md)
