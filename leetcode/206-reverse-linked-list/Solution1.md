# 206. Reverse Linked List 
[&larr;&nbsp;Back to problem](./README.md)

## Approach 1: Iterative

Assume that we have linked list `1 → 2 → 3 → Ø`, we would like to change it to `Ø ← 1 ← 2 ← 3`.

While you are traversing the list, change the current node's next pointer to point to its previous element. Since a node does not have reference to its previous node, you must store its previous element beforehand. You also need another pointer to store the next node before changing the reference. Do not forget to return the new head reference at the end!

### Implementation

```Java
public ListNode reverseList(ListNode head) {
    ListNode prev = null;
    ListNode curr = head;
    while (curr != null) {
        ListNode nextTemp = curr.next;
        curr.next = prev;
        prev = curr;
        curr = nextTemp;
    }
    return prev;
}
```

### Complexity Analysis

* Time complexity : $$\mathcal{O}(n)$$. Assume that nn is the list's length, the time complexity is $$\mathcal{O}(n)$$.
* Space complexity : $$\mathcal{O}(1)$$.

