# 2. [add two numbers](https://leetcode.com/problems/add-two-numbers/description/) 
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, with each node containing a single digit. Add the two numbers and return the sum as a linked list. You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## solution

When I read the title of this problem, I thought I could just write `return x + y` and call it a day, but sadly that is not the case.

In my early school days, we would add numbers using vertical addition, and I think a similar concept can be used for this problem.

We can iterate through the nodes of the linked lists and add the two numbers digit by digit. Using modulo, we can get the individual digit of the sum, and using floor division, we can calculate the carry.

We keep adding digits until we've iterated through all the nodes in the linked lists and are left with no carries. Our result will be stored in a new linked list.

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution(object):
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        node = ListNode()
        result = node

        total = 0
        carry = 0

        while l1 or l2 or carry:
            total = carry
            if l1:
                total += l1.val
                l1 = l1.next
            if l2:
                total += l2.val
                l2 = l2.next

            value = total % 10
            carry = total // 10
            node.next = ListNode(value)
            node = node.next

        return result.next
```

**Time complexity:** O(m + n) | **Space Complexity:** O(max(m, n)), where m and n are the lengths of the given linked lists.
