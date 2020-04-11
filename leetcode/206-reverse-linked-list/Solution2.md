# 206. Reverse Linked List 
[&larr;&nbsp;Back to problem](./README.md)

## Approach 2: Recursive

The recursive version is slightly trickier and the key is to work backwards. Assume that the rest of the list had already been reversed, now how do I reverse the front part? Let's assume the list is: n<sub>1</sub> → … → n<sub>k-1</sub> → n<sub>k</sub> → n<sub>k+1</sub> → … → n<sub>m</sub> → Ø

Assume from node n<sub>k+1</sub> to nm had been reversed and you are at node n<sub>k</sub>.

n<sub>1</sub> → … → n<sub>k-1</sub> → **n<sub>k</sub>** → n<sub>k+1</sub> ← … ← n<sub>m</sub>

We want n<sub>k+1</sub>’s next node to point to nk.

So,

n<sub>k</sub>.next.next = n<sub>k</sub>;

Be very careful that n1's next must point to Ø. If you forget about this, your linked list has a cycle in it. This bug could be caught if you test your code with a linked list of size 2.

### Implementation

```Java
public ListNode reverseList(ListNode head) {
    if (head == null || head.next == null) return head;
    ListNode p = reverseList(head.next);
    head.next.next = head;
    head.next = null;
    return p;
}
```

### Complexity Analysis

* Time complexity : $$\mathcal{O}(n)$$. Assume that $$n$$ is the list's length, the time complexity is $$\mathcal{O}(n)$$.
* Space complexity : $$\mathcal{O}(n)$$. The extra space comes from implicit stack space due to recursion. The recursion could go up to $$n$$ levels deep.

